<template>
  <div class="documents">
    <ul>
      <li v-for="document in documents" :key="document.id">
        <div class="icon">
          <FolderIcon />
        </div>
        <div class="document">
          <span>{{ document.name }}</span>
          <span>{{ document.id }}</span>
        </div>
      </li>
    </ul>
    <a href="#">Ver todos</a>
  </div>
</template>

<script>
import FolderIcon from '@/assets/folder.svg'

export default {
  name: 'Documents',
  components: {
    FolderIcon
  },
  data() {
    return {
      documents: [
          {
            id: 2356833,
            name: 'Calendário @2020'
          },
          {
            id: 2356821,
            name: 'Contas Bancarias'
          },
          {
            id: 2339190,
            name: 'Checkpoint 3'
          }
      ]
    }
  }
}
</script>

<style scoped lang="scss">
  .documents {
    ul {
      margin: 0;
      padding: 0;
      list-style: none;

      li {
        margin-bottom: 20px;

        &:last-child {
          margin-bottom: 0;
        }

        > div {
          display: inline-block;
        }
      }
    }

    a {
      float: right;
      font-size: 16px;
      line-height: 19px;
      text-decoration: none;
      color: #74b9ff;
    }

    .icon {
      svg {
        path {
          fill: #b4b4b4;
        }
      }
    }

    .document {
      margin-left: 15px;

      span {
        display: block;
        font-size: 16px;
        line-height: 19px;
        color: #555;
      }
    }
  }
</style>
