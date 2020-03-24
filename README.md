# chinese-synonym-word

#### 功能
中文常用词同义词|同类词|近义词， 同类词与近义词不严格区分


#### 安装
```buildoutcfg
pip install chinese-synonym-word==0.1.6
```

#### 使用
```buildoutcfg
from chinese_synonym_word.chinese_synonym_word import chinese_synonym_word

# 同义词
chinese_synonym_word.get_synonym_word_cl("桌子"，is_strict=True)
# ['桌子', '台子', '案子', '桌', '台', '案', '几']

# 同类词
chinese_synonym_word.get_synonym_word_cl("桌子"，is_strict=False)
# ['桌子', '台子', '案子', '桌', '台', '案', '几', '方桌', '八仙桌', '四仙桌', '圆桌', '圆台', '书桌', '书案', '写字台', '办公桌', '一头儿沉', '桌案', '梳妆台', '镜台', '条案', '条桌', '条几', '六仙桌', '炕桌', '餐桌', '供桌', '香案', '公案', '茶几', '三屉桌', '会议桌', '饭桌', '炕几', '茶桌', '长桌', '木桌', '谈判桌', '课桌', '围桌', '画案', '服务台', '乒乓球台', '售票台', '化验台', '柜台', '机台', '交换台', '球台', '手术台', '地震台', '圆桌面', '桌面', '桌椅', '桌椅板凳']

# 近义词
chinese_synonym_word.get_synonym_word_vec("桌子")
# ['椅子', '茶几', '凳子', '桌面', '方桌', '书桌', '桌', '办公桌', '写字台']

```
 
