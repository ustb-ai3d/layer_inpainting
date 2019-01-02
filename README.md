# layer_inpainting 

Updated 12-28 Bingmang:
- 更新像场模拟数据的对比
- [add] phase_compare.py
- [rename] main.py -> phase_mat_inpaint.py 

Updated 12-23 MATony:
- 更新imageUtility工具
- 更新表面积计算函数
- 更新腐蚀边缘的函数
 

TODO:
- 添加处理过程信息
- 加快间隔超过4的处理速度
- 对比统计信息（体积、表面积等）

#### layer_inpainting/inpaint.py
```
Usage: python inpaint.py

Example:
    data/
        - interval
            - Pha1_00020_value/
                -X_Z
                    - interval_1/
                        - 000.png
                        - 001.png
                        ...
                    - interval_2/
                    - interval_3/
        - original
            - mat
                - Pha1_00001_value.mat
                ...
            - Pha1_00001_value.txt
            ...
    result/
        - NS/
            - Pha1_00020_value/
                - images/
                    - interval_1/
                        - 000.png
                        - 001.png
                        ...
                    - interval_2/
                    - interval_3/
                - interval_1.mat
                - interval_2.mat
                - interval_3.mat
                ...
```

#### phase_txt2mat.py
```
Usage: python phase_txt2mat.py --input data --output result --cpus 4

Example:
    data/
        - Pha1_00000_value.txt
        - Pha1_00001_value.txt
        ...
    result/
        - Pha1_00000_value.mat
        - Pha1_00001_value.mat
        ...
```


#### phase_mat_inpaint.py
```
Usage: python main.py --input mat_folder --output result --cpus 4

Example:
    mat_folder/
        - Pha1_00000_value.mat
        - Pha1_00001_value.mat
        ...
    result/
        - Pha1_00020_value/
            - Origin/
                - 000.png
                - 001.png
                ...
            - Interval/
                - interval_1/
                    - 000.png
                    - 001.png
                    ...
                - interval_2/
                - interval_3/
            - NS/
                - images/
                    - interval_1/
                        - 000.png
                        - 001.png
                        ...
                    - interval_2/
                    - interval_3/
                - interval_1.mat
                - interval_2.mat
                - interval_3.mat
                ...
```


#### phase_compare.py
```
"""
对比原始mat和修复后的mat的体积及表面积

Usage: python phase_compare.py --data ./data --result ./result --mode TELEA

"""

Output:
    Pha1_00020_value origin volume: 28523167, interval_1 volume: 28609898, error: 0.3041, accuracy: 99.6959
    Pha1_00020_value origin volume: 28523167, interval_10 volume: 28559278, error: 0.1266, accuracy: 99.8734
    Pha1_00020_value origin volume: 28523167, interval_15 volume: 29260030, error: 2.5834, accuracy: 97.4166
    Pha1_00020_value origin volume: 28523167, interval_2 volume: 28577997, error: 0.1922, accuracy: 99.8078
    Pha1_00020_value origin volume: 28523167, interval_20 volume: 29537153, error: 3.5545, accuracy: 96.445
    Pha1_00020_value origin volume: 28523167, interval_4 volume: 28629146, error: 0.3716, accuracy: 99.6284
    Pha1_00020_value origin volume: 28523167, interval_6 volume: 28634186, error: 0.3892, accuracy: 99.6108
    Pha1_00020_value origin surface: 4756327, interval_4 surface: 4658672, error: 2.0532, accuracy: 97.9468
    Pha1_00020_value origin surface: 4756327, interval_1 surface: 4720437, error: 0.7546, accuracy: 99.2454
    Pha1_00020_value origin surface: 4756327, interval_10 surface: 4514900, error: 5.0759, accuracy: 94.9241
    Pha1_00020_value origin surface: 4756327, interval_2 surface: 4724372, error: 0.6718, accuracy: 99.3282
    Pha1_00020_value origin surface: 4756327, interval_15 surface: 4322647, error: 9.118, accuracy: 90.882
    Pha1_00020_value origin surface: 4756327, interval_6 surface: 4603914, error: 3.2044, accuracy: 96.7956
    Pha1_00020_value origin surface: 4756327, interval_20 surface: 4448497, error: 6.4720, accuracy: 93.528
```
