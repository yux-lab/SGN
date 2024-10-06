following 原教程，修改. so 路径


requirements
```bash
yapf==0.40.1
setuptools==59.5.0
```

将 save_flag=False 改成 True
设置 pred 路径
CTRL + F ：modified by

存疑
`mmcv.dump(outputs['bbox_results'], args.out)` -> `mmcv.dump(outputs, args.out)`