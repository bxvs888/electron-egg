<template>
  <div>
    <h3 :style="{ marginBottom: '16px' }">
      demo1 打开文件夹实现
    </h3>
    <a-list bordered :data-source="data">
      <a-list-item @click="openDirectry(item.id)" slot="renderItem" slot-scope="item">
        {{ item.content }}
        <a-button type="link">
          打开
        </a-button>
      </a-list-item>
    </a-list>
  </div>
</template>
<script>
import { localApi } from '@/api/main'

const data = [
  {
    content: '【下载】目录',
    id: 'download'
  },
  {
    content: '【图片】目录',
    id: 'picture'
  },
  {
    content: '【文档】目录',
    id: 'doc'
  },
  {
    content: '【音乐】目录',
    id: 'music'
  }
];

export default {
  data() {
    return {
      data,
    };
  },
  methods: {
    openDirectry (id) {
      console.log('id:', id)
      const params = {
        'id': id
      }
      localApi('openDir', params).then(res => {
        if (res.code !== 0) {
          return false
        }
      }).catch(err => {
        console.log('err:', err)
      })
    },
  }
};
</script>
<style></style>
