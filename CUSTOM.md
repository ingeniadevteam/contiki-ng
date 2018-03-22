# Contiki custom changes



## The ARM GCC toolchain

Download arm-gcc-eabi- for Linux from [Launchpad](https://launchpad.net/gcc-arm-embedded/+download).
Unzip to your home directory (in Linux)
Update PATH variable (version may be changed):
```bash
echo "export PATH=\$PATH:/home/victor/gcc-arm-none-eabi-5_4-2016q3/bin" >> ~/.bashrc
# log out and back in
```

## Custom build

```
git clone --recursive --depth 1 https://github.com/ingeniadevteam/contiki-ng.git
cd contiki-ng
git submodule sync && git submodule update --init

cd examples/platform-specific/cc26xx
BOARD=sensortag/cc2650 make
```

## Custom changes made to contiki

/home/victor/proyectos/contiki-ng/arch/cpu/cc26xx-cc13xx/rf-core/rf-ble.c
```c
/* BLE Intervals: Send a burst of advertisements every BLE_ADV_INTERVAL secs */
#define BLE_ADV_INTERVAL      (CLOCK_SECOND * 10) // 5
#define BLE_ADV_DUTY_CYCLE    (CLOCK_SECOND / 10)
#define BLE_ADV_MESSAGES      1   // 10
```
