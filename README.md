# Introduction 
this file gives instructions on how to run this project. <br>
because the code repository is too large for direct uploading here, it's shared via figshare. <br>
click on the following link and download the code zip:<br>
link: 
https://figshare.com/s/7aec193ade959d6a2c97 <br>
the above link redirects to figshare page, just click on the downloading icon on the page to download.<br>
After downloading the .zip file, unzip it. <br>
the unzipped folder is the full code folder, there is a readme file in it which is same as below:<br>

the weight files are also included, <br>
so you can directly run the attacks based on loaded weights by directly running the "run attacks" part, <br>
or you can also choose to pre-train models from scratch, by firstly running the "pre-training" part.<br>

## Package required

this project was mainly ran on google colab (linux) with default settings, <br>
but they are also runnable on Windows, default conda3 environment after my testings. <br>

because it is not a permanent way to store and run the codes on google colab, 
I transferred them to Windows (the following instructions are based on Windows) <br>

thus, the environment settings of this Windows were export to "requirments.txt", 
but normally the default latest versions of tools should be fine. <br>

to run these codes on Windows:<br>

    Python Version: 3.12.3
Package Dependencies: see `requirements.txt`<br>
To install dependencies:

    pip install -r requirements.txt
if this way does not work (sometimes), install dependencies manually: <br> 

    PyTorch：2.5.1
    TorchVision：0.20.1
    Torchaudio：2.5.1
    TorchMetrics：1.6.3
    Matplotlib：3.9.2
    TQDM：4.66.5
    Pandas：2.2.2
    NumPy：1.26.4
    SciPy：1.13.1
    Scikit-learn：1.5.1
    Seaborn：0.13.2

note, before running each code cell, make sure you stay at the root directory of this project,
as the paths below are relative paths to the root. <br>
normally you can use "cd../../" or "cd../" to return to the root after running a cell.

# run attacks

## APA attack 
(approx. 10-30 min for each run)

### run APA attack to our method
    cd ./mydefense/cifar10_resnet32
    python adv_param_attack.py
similar for other datasets and model types (just replace names of dataset and model type).

### to base models
    cd ./mydefense/cifar10_resnet32
    python adv_param_attack.py --load_path '../../cifar10/resnet32/save/model_best.pth.tar'
similar for other datasets and model types.

### to Aegis
    cd ./mydefense/cifar10_resnet32
    python adv_param_attack.py --load_path '../../cifar10/resnet32/save_finetune/model_best.pth.tar'
similar for other datasets and model types.

### to BIN
    cd ./bin/cifar10_resnet32
    python adv_param_attack.py
similar for other datasets and model types.

### to SDN
    cd ./sdn/cifar10_resnet32
    python adv_param_attack.py
similar for other datasets and model types.

## P3A attack
(approx. less than 5 min for each run)

### run P3A attack to our method
    cd ./mydefense/cifar10_resnet32
    python spa.py
similar for other datasets and model types.

### to base models
    cd ./mydefense/cifar10_resnet32
    python spa.py --load_path '../../cifar10/resnet32/save/model_best.pth.tar'
similar for other datasets and model types.

### to Aegis
    cd ./mydefense/cifar10_resnet32
    python spa.py --load_path '../../cifar10/resnet32/save_finetune/model_best.pth.tar'
similar for other datasets and model types.

### to BIN
    cd ./bin/cifar10_resnet32
    python spa.py
similar for other datasets and model types.

### to SDN
    cd ./sdn/cifar10_resnet32
    python spa.py
similar for other datasets and model types.

## PGD attack
(approx. less than 10 min for each run)

### run PGD attack to our method
    cd ./mydefense/cifar10_resnet32
    python adv_pdg.py
similar for other datasets and model types.

### to base models
    cd ./mydefense/cifar10_resnet32
    python adv_pdg.py --load_path '../../cifar10/resnet32/save/model_best.pth.tar'
similar for other datasets and model types.

### to Aegis
    cd ./mydefense/cifar10_resnet32
    python adv_pdg.py --load_path '../../cifar10/resnet32/save_finetune/model_best.pth.tar'
similar for other datasets and model types.

### to BIN
    cd ./bin/cifar10_resnet32
    python adv_pgd.py
similar for other datasets and model types.

### to SDN
    cd ./sdn/cifar10_resnet32
    python adv_pgd.py
similar for other datasets and model types.

## TBT attack
(approx. 6-20 min for each run)

### run TBT attack to our method
    cd ./TBT/resnet32-cifar10
    python TBT_adaptive.py
similar for other datasets and model types.

### to base models
    cd ./TBT/resnet32-cifar10
    python TBT_adaptive.py --load_path '../../cifar10/resnet32/save/model_best.pth.tar'
similar for other datasets and model types.

### to Aegis
    cd ./TBT/resnet32-cifar10
    python TBT_adaptive.py --load_path '../../cifar10/resnet32/save_finetune/model_best.pth.tar'
similar for other datasets and model types.

### to SDN
    cd ./sdn/cifar10_resnet32
    python tbt_ada.py
similar for other datasets and model types.

# pre-training
note, the pre-training works of base model and aegis were ran on old environments at the beginning of experiment.<br>
so they are not necessarily fine with current latest environment (normally they should be) <br>
thus, if the pre-training works of base model and aegis cannot work normally, maybe try following old environments:

    python 3.6.9, pytorch 1.7.0, torchvision 0.8.1, tensorboardX 2.5, matplotlib 3.3.4, tqdm 4.60.0, pandas 1.1.5, numpy 1.18.5.

experiments other than pre-training of base model and aegis should all work.

### pretrain target models
(approx. 2-3 hours for each run)

    cd cifar10/resnet32
    sh train_CIFAR.sh
similar for other datasets and model types.

### pretrain attack models
(approx. 1-2 hours for each run)

    cd ./pretrain
    python cifar10-resnet50.py
similar for other datasets and model types.

### fine-tuning target models
(approx. 1.5-2.5 hours for each run)

    cd ./mydefense/cifar10_resnet32
    python train.py
similar for other datasets and model types.

### pretrain Aegis
(approx. 1-2 hours for each run)

    cd ./cifar10/resnet32
    sh train_finetune_branch.sh
similar for other datasets and model types.

### pretrain BIN 
(approx. 1-2 hours for each run)

    cd ./bin/cifar10_resnet32
    python run.py
similar for other datasets and model types.

### pretrain SDN
(approx. 1-2 hours for each run)

    cd ./sdn/cifar10_resnet32
    python run.py
similar for other datasets and model types.

code sources:
part of the above codes were from or modified based on open sources from online, published by auther of original works.<br>
the Aegis and BIN models, and tbt part: https://github.com/vul337/Aegis/blob/main/README.md<br>
the SDN part: https://github.com/yigitcankaya/Shallow-Deep-Networks<br>
the APA attack modified based on: https://github.com/AI-secure/Adversarial-Parameter-Attack<br>
the P3A attack modified based on: https://anonymous.4open.science/r/P3A-A12C/README.md<br>

the implementation of my own defense was completely original.
