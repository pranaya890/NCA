Ctrl+Shift+R= side by side terminal
for turning the keyboard light
```Bash
xset led 3
xset led 3 led off #for turning off
```


```
sudo sh -c 'echo 1 > /sys/class/leds/input71::scrolllock/brightness'
sudo sh -c 'echo 0 > /sys/class/leds/input71::scrolllock/brightness' 
```

``` Shell
# for turning on 
for led in /sys/class/leds/*scrolllock*; do
    echo "=== $led ==="
    cat "$led/max_brightness"
    echo none | sudo tee "$led/trigger"
    echo 255 | sudo tee "$led/brightness"
done

# for turning off 
echo 0 | sudo tee /sys/class/leds/input33::scrolllock/brightness


```