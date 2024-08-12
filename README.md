

--------------------------------


# Deploying a Contract on Fuel Network 
![image](https://github.com/kotipichla/fuel-network/assets/152254884/3644c29d-8e47-4cd5-94b9-18b177946ccf)






## Install Dependencies 

```
sudo apt update
sudo apt upgrade -y
sudo apt-get install curl screen -y 
```


## Installing RUST

```
curl --proto '=https' --tlsv1.3 https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env
rustc --version
```


![image](https://github.com/kotipichla/fuel-network/assets/152254884/6780a448-1989-46ec-9ea3-000c4d1a4fb0)


```
rustup install stable
rustup update stable
rustup default stable
```
![image](https://github.com/kotipichla/fuel-network/assets/152254884/4acf895c-1ffd-4c93-beba-730b1a1a376b)



## Install GIT 

![image](https://github.com/kotipichla/fuel-network/assets/152254884/0bf622bb-87e1-45a9-8673-9e5b0dae8fa9)

```
sudo apt install git -y 
```


## Install Fuel Toolchain 

![image](https://github.com/kotipichla/fuel-network/assets/152254884/a9a66408-9ec9-46c3-bd55-6de6acc0bbd4)

```
curl https://install.fuel.network | sh
```

## press ```y``` then enter
![image](https://github.com/kotipichla/fuel-network/assets/152254884/f6784c41-5aa1-42d5-9c34-b91438ca1f42)



 ### Setting PATH 
![image](https://github.com/kotipichla/fuel-network/assets/152254884/f6bb3cb7-40e4-4064-b537-bd3b40c4edfe)

```
source /root/.bashrc
```


## Setting ```FUELUP```

```
fuelup toolchain install latest
fuelup self update
fuelup update && fuelup default latest
```




## Creating PROJECT 
![image](https://github.com/kotipichla/fuel-network/assets/152254884/ed16a92e-bffe-4808-89d4-76701a1e3995)

```
mkdir fuel-project && cd fuel-project
forc new counter-contract
```



## Editing Contract 


```
nano counter-contract/src/main.sw
```

Clear/delete everything and paste below ```code```

```
contract;
 
storage {
    counter: u64 = 0,
}
 
abi Counter {
    #[storage(read, write)]
    fn increment();
 
    #[storage(read)]
    fn count() -> u64;
}
 
impl Counter for Contract {
    #[storage(read)]
    fn count() -> u64 {
        storage.counter.read()
    }
 
    #[storage(read, write)]
    fn increment() {
        let incremented = storage.counter.read() + 1;
        storage.counter.write(incremented);
    }
}
```


## Save and exit with  ```Ctrl X + y ```  and click ``` ENTER ``` 

--------------------------------------




## Build Contract 
![image](https://github.com/kotipichla/fuel-network/assets/152254884/34f12af3-ee3a-4e90-8fa8-cd48fdec75c7)

```
cd counter-contract
forc build 
```

## Deploying Contract 
Remember, you will need your FUEL wallet here, i will be importing mine, if you don't have wallet, [Install from here](https://wallet.fuel.network/docs/install/)

![image](https://github.com/kotipichla/fuel-network/assets/152254884/bd7aae5b-f0a2-4064-8f6f-54bcdc8f22f6)



## Importing wallet 


```
forc wallet import 
```

## and copy and paste on terminal
![image](https://github.com/kotipichla/fuel-network/assets/152254884/19f7a077-14e2-4231-bdbd-bbaa20e6dc72)

## Note:  ``` password are always invincible```

----------------


## Create Account 

```
forc wallet account new
```
## Import account and input password 



## Check Address 

```
forc wallet accounts
```


---------

## Deploy Contract 

```
forc deploy --testnet 
```

## Enter ```0``` as Index and click ```y``` 

# CONTRACT DEPLOYED 
----------


# EXPLORER 
[FUEL EXPLORER](https://app.fuel.network/) 

-------------










