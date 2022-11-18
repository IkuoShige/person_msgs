# person_msgs
ros2 package

# パッケージ削除方法

例：person_msgのパッケージを削除したい

1.ros2_wsディレクトリ直下のbuild install log ディレクトリの中身を削除(ディレクトリごと削除してもcolcon buildでまた作られる)

```
rm -rf build/person_msg/ install/person_msg/ log/
```

2.colcon buildで使用される環境変数に含まれるパスを削除する

環境変数に記述されたままだと以下のような警告文が出力される

```
[0.170s] WARNING:colcon.colcon_ros.prefix_path.ament:The path '/home/ikuo/robo_sys/ros2_ws/install/person_msg' in the environment variable AMENT_PREFIX_PATH doesn't exist
[0.170s] WARNING:colcon.colcon_ros.prefix_path.catkin:The path '/home/ikuo/robo_sys/ros2_ws/install/person_msg' in the environment variable CMAKE_PREFIX_PATH doesn't exist
```

パッケージのパスが含まれる環境変数を削除すると警告文は出てこなくなる

```
env | grep ros2
```
上記のコマンドでAMENT_PREFIX_PATHとCMAKE_PREFIX_PATHの環境変数が出力できる

出力結果の一部を抜粋し、掲載する

```
AMENT_PREFIX_PATH="/home/ikuo/robo_sys/ros2_ws/install/person_msgs:/home/ikuo/robo_sys/ros2_ws/install/person_msgs:/home/ikuo/robo_sys/ros2_ws/install/mypkg:/opt/ros/foxy"
CMAKE_PREFIX_PATH="/home/ikuo/robo_sys/ros2_ws/install/person_msgs:/home/ikuo/robo_sys/ros2_ws/install/person_msgs"
```

```
export AMENT_PREFIX_PATH="/home/ikuo/robo_sys/ros2_ws/install/person_msgs:/home/ikuo/robo_sys/ros2_ws/install/mypkg:/opt/ros/foxy"
export CMAKE_PREFIX_PATH="/home/ikuo/robo_sys/ros2_ws/install/person_msgs"
```
で変更ができる
