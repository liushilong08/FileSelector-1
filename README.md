# 安卓文件选择器

用法：

### 1.通过Intent打开文件选择器

```java
  Intent intent = new Intent(this, FileSelectorActivity.class);
  intent.putExtra(FileSelectorActivity.ACTIVITY_KEY_MULTI, true);  //是否多选模式
  intent.putExtra(FileSelectorActivity.ACTIVITY_KEY_MAX_COUNT, 3);//限定文件选择数
  intent.putExtra(FileSelectorActivity.ACTIVITY_KEY_FILEROOT, ""); //初始路径
  intent.putExtra(FileSelectorActivity.ACTIVITY_KEY_FILE_TYPE, ""); //筛选文件类型
//intent.putExtra(FileSelectorActivity.ACTIVITY_KEY_FILE_TYPE, FileSelectorActivity.FILE_TYPE_IMAGE);//只展示图片
  startActivityForResult(intent, 100);
```

### 2.在onActivityResult获取结果

```java
    @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        if (resultCode == Activity.RESULT_OK && requestCode == 100 && data != null) {
            try {
                ArrayList<String> pathList = data.getStringArrayListExtra(FileSelectorActivity.ACTIVITY_KEY_RESULT_PATHLIST);
                for (String path : pathList) {
                    Log.i(TAG, path);
                }
            } catch (Exception e) {
            }
        }
    }
```
