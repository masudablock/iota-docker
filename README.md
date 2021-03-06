# Edge server application

get sample point cloud data.
set up the edge server application for blockchain.

# How to setup
## For development evironmenet

This information is for a development environmenet. It is assumed PC or virtual machine.

### Reuquired specification
- 8GB or upper RAM
- A dual-core or upper CPU
- Ubuntu 18.04, MacOS X or Later

### install homebrew

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
if "Press RETURN to continue or any other key to abort" is shown, press RETURN.

### build virtual machine

```
$ brew cask install virtualbox
$ brew cask install vagrant
$ brew install wget
$ wget https://app.vagrantup.com/ubuntu/boxes/bionic64/versions/20210125.0.0/providers/virtualbox.box
$ vagrant init bento/ubuntu-18.04
$ vagrant up
$ vagrant ssh
```

### Install nodejs

```
$ cd /vagrant
$ sudo apt install nodejs npm
```

### Download souce code

```
$ git clone https://github.com/masudablock/Edge-server-application.git
```

### create sample data

```
$ cd Edge-server-application
$ chmod 755 set_up.sh
$ ./set_up.sh 
```

### Setup Edge server application

```
python3 main.py
```

# Information

- http request
    - port
        - http://localhost:4001/api/set
    - Content-Type
        - application/json

```
{
    "camera_id": num,
    frame_number": num,
    "hash": sha256,
    "execute": any,
}
```

- Parameters
    - camera_id
        - This is cammera ID number.
    - frame_number
        - This is a current frame number
    - hash
        - This is stack hashed camera data.
        - Hash algorithm is sha256.
    - execute
        - This is flag of execution.
        - If this parameter exists, writing function to blockchain is executed.
       
- About hash
    - This is hashed camera raw data.
    - 3 frames example
        1. Create hash of first frame from raw image data.
        2. Add the previous transaction hash and first hash. - (A)
        3. Create hash of sececond frame.
        4. Add (A) and second hash. -(B)
        5. Hash (B). - (C)
        6. Create hash of third frame.
        7. Add (C) to third hash. - (D)
        8. (D) is final hash. This hash will store the blockchain.






