## Image

Besides the native features of img, support lazy load, custom placeholder and load failure, etc.

### Basic Usage

:::demo Indicate how the image should be resized to fit its container by `fit`, same as native [object-fit](https://developer.mozilla.org/en-US/docs/Web/CSS/object-fit)。

```html
<div class="demo-image">
  <div class="block" v-for="fit in fits" :key="fit">
    <span class="demonstration">{{ fit }}</span>
    <el-image
      style="width: 100px; height: 100px"
      :src="url"
      :fit="fit"
    ></el-image>
  </div>
</div>

<script>
  export default {
    data() {
      return {
        fits: ['fill', 'contain', 'cover', 'none', 'scale-down'],
        url: 'https://fuss10.elemecdn.com/e/5d/4a731a90594a4af544c0c25941171jpeg.jpeg',
      }
    },
  }
</script>
<!--
<setup>

  import { defineComponent, reactive, toRefs } from 'vue';

  export default defineComponent({
    setup() {
      const state = reactive({
        fits: ['fill', 'contain', 'cover', 'none', 'scale-down'],
        url: 'https://fuss10.elemecdn.com/e/5d/4a731a90594a4af544c0c25941171jpeg.jpeg'
      });

      return {
        ...toRefs(state),
      };
    },
  });
</setup>
-->
```

:::

### Placeholder

:::demo Custom placeholder content when image hasn't loaded yet by `slot = placeholder`

```html
<div class="demo-image__placeholder">
  <div class="block">
    <span class="demonstration">Default</span>
    <el-image :src="src"></el-image>
  </div>
  <div class="block">
    <span class="demonstration">Custom</span>
    <el-image :src="src">
      <template #placeholder>
        <div class="image-slot">Loading<span class="dot">...</span></div>
      </template>
    </el-image>
  </div>
</div>

<script>
  export default {
    data() {
      return {
        src: 'https://cube.elemecdn.com/6/94/4d3ea53c084bad6931a56d5158a48jpeg.jpeg',
      }
    },
  }
</script>
<!--
<setup>

  import { defineComponent, ref } from 'vue';

  export default defineComponent({
    setup() {
      const src = ref('https://cube.elemecdn.com/6/94/4d3ea53c084bad6931a56d5158a48jpeg.jpeg');

      return {
        src,
      };
    },
  });

</setup>
-->
```

:::

### Load Failed

:::demo Custom failed content when error occurs to image load by `slot = error`

```html
<div class="demo-image__error">
  <div class="block">
    <span class="demonstration">Default</span>
    <el-image></el-image>
  </div>
  <div class="block">
    <span class="demonstration">Custom</span>
    <el-image>
      <template #error>
        <div class="image-slot">
          <i class="el-icon-picture-outline"></i>
        </div>
      </template>
    </el-image>
  </div>
</div>
```

:::

### Lazy Load

:::demo Use lazy load by `lazy = true`. Image will load until scroll into view when set. You can indicate scroll container that adds scroll listener to by `scroll-container`. If undefined, will be the nearest parent container whose overflow property is auto or scroll.

```html
<div class="demo-image__lazy">
  <el-image v-for="url in urls" :key="url" :src="url" lazy></el-image>
</div>

<script>
  export default {
    data() {
      return {
        urls: [
          'https://fuss10.elemecdn.com/a/3f/3302e58f9a181d2509f3dc0fa68b0jpeg.jpeg',
          'https://fuss10.elemecdn.com/1/34/19aa98b1fcb2781c4fba33d850549jpeg.jpeg',
          'https://fuss10.elemecdn.com/0/6f/e35ff375812e6b0020b6b4e8f9583jpeg.jpeg',
          'https://fuss10.elemecdn.com/9/bb/e27858e973f5d7d3904835f46abbdjpeg.jpeg',
          'https://fuss10.elemecdn.com/d/e6/c4d93a3805b3ce3f323f7974e6f78jpeg.jpeg',
          'https://fuss10.elemecdn.com/3/28/bbf893f792f03a54408b3b7a7ebf0jpeg.jpeg',
          'https://fuss10.elemecdn.com/2/11/6535bcfb26e4c79b48ddde44f4b6fjpeg.jpeg',
        ],
      }
    },
  }
</script>
<!--
<setup>
  import { defineComponent, ref } from 'vue';

  export default defineComponent({
    setup() {
      const urls = ref([
        'https://fuss10.elemecdn.com/a/3f/3302e58f9a181d2509f3dc0fa68b0jpeg.jpeg',
        'https://fuss10.elemecdn.com/1/34/19aa98b1fcb2781c4fba33d850549jpeg.jpeg',
        'https://fuss10.elemecdn.com/0/6f/e35ff375812e6b0020b6b4e8f9583jpeg.jpeg',
        'https://fuss10.elemecdn.com/9/bb/e27858e973f5d7d3904835f46abbdjpeg.jpeg',
        'https://fuss10.elemecdn.com/d/e6/c4d93a3805b3ce3f323f7974e6f78jpeg.jpeg',
        'https://fuss10.elemecdn.com/3/28/bbf893f792f03a54408b3b7a7ebf0jpeg.jpeg',
        'https://fuss10.elemecdn.com/2/11/6535bcfb26e4c79b48ddde44f4b6fjpeg.jpeg',
      ]);

      return {
        urls,
      };
    },
  });

</setup>
-->
```

:::

### Image Preview

:::demo allow big image preview by setting `previewSrcList` prop.

```html
<div class="demo-image__preview">
  <el-image
    style="width: 100px; height: 100px"
    :src="url"
    :preview-src-list="srcList"
  >
  </el-image>
</div>

<script>
  export default {
    data() {
      return {
        url: 'https://fuss10.elemecdn.com/e/5d/4a731a90594a4af544c0c25941171jpeg.jpeg',
        srcList: [
          'https://fuss10.elemecdn.com/8/27/f01c15bb73e1ef3793e64e6b7bbccjpeg.jpeg',
          'https://fuss10.elemecdn.com/1/8e/aeffeb4de74e2fde4bd74fc7b4486jpeg.jpeg',
        ],
      }
    },
  }
</script>
<!--
<setup>

  import { defineComponent, ref } from 'vue';

  export default defineComponent({
    setup() {
      const url = ref('https://fuss10.elemecdn.com/e/5d/4a731a90594a4af544c0c25941171jpeg.jpeg');
      const srcList = ref([
        'https://fuss10.elemecdn.com/8/27/f01c15bb73e1ef3793e64e6b7bbccjpeg.jpeg',
        'https://fuss10.elemecdn.com/1/8e/aeffeb4de74e2fde4bd74fc7b4486jpeg.jpeg',
      ]);

      return {
        url,
        srcList,
      };
    },
  });

</setup>
-->
```

:::

### Image Attributes

| Attribute           | Description                                                                                                                                      | Type                 | Accepted values                            | Default                                                                |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------- | ------------------------------------------ | ---------------------------------------------------------------------- |
| alt                 | Native alt                                                                                                                                       | string               | -                                          | -                                                                      |
| fit                 | Indicate how the image should be resized to fit its container, same as [object-fit](https://developer.mozilla.org/en-US/docs/Web/CSS/object-fit) | string               | fill / contain / cover / none / scale-down | -                                                                      |
| hide-on-click-modal | When enabling preview, use this flag to control whether clicking on backdrop can exit preview mode                                               | boolean              | true / false                               | false                                                                  |
| lazy                | Whether to use lazy load                                                                                                                         | boolean              | —                                          | false                                                                  |
| preview-src-list    | allow big image preview                                                                                                                          | Array                | —                                          | -                                                                      |
| referrer-policy     | Native referrerPolicy                                                                                                                            | string               | -                                          | -                                                                      |
| src                 | Image source, same as native                                                                                                                     | string               | —                                          | -                                                                      |
| scroll-container    | The container to add scroll listener when using lazy load                                                                                        | string / HTMLElement | —                                          | The nearest parent container whose overflow property is auto or scroll |
| z-index             | set image preview z-index                                                                                                                        | Number               | —                                          | 2000                                                                   |

### Image Events

| Event Name | Description          | Parameters |
| ---------- | -------------------- | ---------- |
| load       | Same as native load  | (e: Event) |
| error      | Same as native error | (e: Error) |

### Image Slots

| Name        | Description                     |
| ----------- | ------------------------------- |
| placeholder | Triggers when image load        |
| error       | Triggers when image load failed |

### ImageViewer Attributes

| Attribute           | Description                                                                                                                  | Type            | Acceptable Value    | Default |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------- | --------------- | ------------------- | ------- |
| url-list            | Preview link list                                                                                                            | Array\<string\> | -                   | []      |
| z-index             | Preview backdrop z-index                                                                                                     | number / string | int / string\<int\> | 2000    |
| initial-index       | The initial preview image index, less than or equal to the length of `url-list`                                              | number          | int                 | 0       |
| infinite            | Whether preview is infinite                                                                                                  | boolean         | true / false        | true    |
| hide-on-click-modal | Whether user can emit close event when clicking backdrop                                                                     | boolean         | true / false        | false   |
| append-to-body      | whether to append image itself to body. A nested parent element attribute transform should have this attribute set to `true` | boolean         | —                   | false   |

### ImageViewer Events

| Event name | Description                                                                                    | Callback parameter                     |
| ---------- | ---------------------------------------------------------------------------------------------- | -------------------------------------- |
| close      | Emitted when clicking on `X` button or when `hide-on-click-modal` enabled clicking on backdrop | None                                   |
| switch     | When switching images                                                                          | `(val: number)` switching target index |
