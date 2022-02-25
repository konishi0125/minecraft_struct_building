# minecraft_struct_building
csvの構造物データからマイクラ内に建造物を作成する\
This program struct building in minecraft from csv file.

# 動作環境_Environment
Minecraft Java Edition v1.12.2\
Forge 14.23.5.2855\
Raspberry Jam Mod 0.92

# 使い方_Usage
pipコマンドでインストール
```commandline
pip install minecraft_struct_building
```

## コマンドラインから
```commandline
minecraft_struct_building x y z csv_path --replace_blocks --new_blocks --slice_struct --slice_direction
```
x,y,z:建造物の角の座標　各値は最小値\
x_range,y_range,z_range:x,y,z方向の建造物のサイズ\
csv_path:読み込むcsvのパス\
--replace_blocks:置き換え元のブロック [[id_1, data_1], [id_2,data_2],...]\
--new_blocks:置き換え先のブロック [[id_1, data_1], [id_2,data_2],...]
--slice_struct:端から順番に置くかどうか default:False bool型
--slice_structの方向を決める x,y,z default:y

## スクリプト内で使用
### 基本的な使い方
```python
from minecraft_struct_building import minecraft_struct_building

struct=minecraft_struct_building.Struct()
struct.load_data("csv_path")
struct.struct_building(x,y,z) #x,y,z,は構造物の角の座標
```

### 構成するブロックを置き換える
```python
"""
replace_blocks, new_blocks
ブロックのidとデータのリスト [[id_1, data_1], [id_2,data_2],...]
replace=True:読み込んだデータを書き換える
replace=False:読み込んだデータを書き換えず、置き換えたデータリストを返す
"""
struct.exchange_block(replace_blocks, new_blocks, replace=False)
```
