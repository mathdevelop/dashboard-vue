<template>
  <div id="weather" v-if="weather">
    <h4>{{ weather.city }}</h4>
    <span>{{ weather.datetime }}</span>
    <span>{{ weather.text }}</span>
    <ul>
      <li>
        <RainIcon />
        <span>Chuva {{ weather.rain }}%</span>
      </li>
      <li>
        <WindIcon />
        <span>Umidade {{ weather.humidity }}%</span>
      </li>
      <li>
        <RaindropIcon />
        <span>Vento {{ weather.wind }}km/h</span>
      </li>
    </ul>
  </div>
  <LoadingIcon v-else/>
</template>

<script>
import axios from 'axios';
import LoadingIcon from '@/assets/loading.svg';
import RainIcon from '@/assets/rain.svg';
import WindIcon from '@/assets/wind.svg';
import RaindropIcon from '@/assets/raindrop.svg';

export default {
  components: {
    LoadingIcon,
    RainIcon,
    WindIcon,
    RaindropIcon
  },
  data() {
    return {
      weather: null
    }
  },
  created() {
    //Não utilizei a API recomendada, pois retorna somente o nome completo do Estado, o Climatempo aceita somente sigla
    axios.get('//api.ipstack.com/check?access_key=62b797cc3be795499d3e4f30a86b94e8').then(response => {
      const { city, region_code } = response.data;

      //Utilizando um Proxy, pois o Climatempo utiliza CORS, mesmo após desabilitar no painel
      axios.get(`https://cors-anywhere.herokuapp.com/http://apiadvisor.climatempo.com.br/api/v1/locale/city?name=${ city }&state=${ region_code }&token=bf8defc9be7280bf51d5660b100729af`).then(response => {
        const { id } = response.data.shift(),
              params = new URLSearchParams();

        params.append('localeId[]', id);

        //Climatempo exige que a cidade esteja cadastrada no Token que irá ser utilizado para as consultas
        axios.put('https://cors-anywhere.herokuapp.com/http://apiadvisor.climatempo.com.br/api-manager/user-token/bf8defc9be7280bf51d5660b100729af/locales', params).then(() => {
          //Tive que utilizar a rota dos 15 dias, porque a rota do dia atual não retorna a probabilidade de chuva
          axios.get(`https://cors-anywhere.herokuapp.com/http://apiadvisor.climatempo.com.br/api/v1/forecast/locale/${ id }/days/15?token=bf8defc9be7280bf51d5660b100729af`).then(response => {
            const weather = response.data.data.shift(),
                  weeks = ['Domingo', 'Segunda-Feira', 'Terça-Feira', 'Quarta-Feira', 'Quinta-Feira', 'Sexta-Feira', 'Sábado'],
                  date = new Date();

            this.weather = {
              city: city + ' - ' + region_code,
              datetime: weeks[date.getDay()] + ', ' + date.getHours() + ' horas',
              text: weather.text_icon.text.pt,
              rain: weather.rain.probability,
              humidity: (weather.humidity.min + weather.humidity.max) / 2, //Na rota de 15 dias, não retorna média
              wind: weather.wind.velocity_avg
            };
          });
        });
      });
    });
  }
}
</script>

<style scoped lang="scss">
  #weather {
    h4 {
      margin: 0;
      font-size: 36px;
      line-height: 42px;
      color: #000;
    }

    > span {
      display: block;
    }

    ul {
      margin: 30px 0 0;
      padding: 0;
      list-style: none;

      span {
        margin-left: 5px;
        font-family: 'Rubik', sans-serif;
        font-size: 16px;
        line-height: 19px;
        color: #555;
      }
    }
  }
</style>
