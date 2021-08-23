# pywebio-cpu-memory-disk-test

![Demo](https://streamable.com/q25eg8)

## install
```sh
sudo apt install python3-pip & yum install --assumeyes python3-pip
sudo git clone https://github.com/erelbi/pywebio-cpu-memory-disk-test.git
cd pywebio-cpu-memory-disk-test/
virtualenv venv
source venv/bin/activate
pip3 install -r requirements.txt
```

## run
```sh
python3 main.py 
```

### memory
```python
 cmd=["cat <( </dev/zero head -c {}m) <(sleep 1) | tail".format(amount_of_ram)]
 ```
 
### cpu

````python
def cpu_stress():
    try:
        global time_stress
        old_time = time.time()+ float(time_stress)
        while old_time > time.time():
            processes = cpu_count()
            pool = Pool(processes)
            pool.map(cpu_time, range(processes))
            if time.time() > old_time:
                break
    except Exception as err:
        windows_txt(err)
    
def cpu_time(x):
    try:
        global time_stress
        old_time = time.time()+ float(time_stress)
        while old_time > time.time():
            x*x
    except Exception as err:
        windows_txt(err)
````

### disk

```python
cmd = ['echo {} | su -c "time dd if=/dev/{} of=/test1.txt bs=8k count=300"'.format(root_passwd,btn)]
```



