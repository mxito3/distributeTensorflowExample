git clone https://github.com/mxito3/distributeTensorflowExample && cd distributeTensorflowExample

sudo apt install software-properties-common && sudo add-apt-repository ppa:deadsnakes/ppa && sudo apt update && sudo apt install python3.7 && sudo apt install python3.7-dev && sudo apt install python3.7-venv

python3.7 -m venv venv && source venv/bin/activate && pip install tensorflow

ps 节点执行： 


CUDA_VISIBLE_DEVICES='' python distribute.py --ps_hosts=47.75.243.164:9001 --worker_hosts=8.129.168.22:2224,176.122.128.190:2225 --job_name=ps --task_index=0



worker 节点执行:

CUDA_VISIBLE_DEVICES=0 python distribute.py --ps_hosts=47.75.243.164:9001 --worker_hosts=8.129.168.22:2224,176.122.128.190:2225 --job_name=worker --task_index=0

CUDA_VISIBLE_DEVICES=0 python distribute.py --ps_hosts=47.75.243.164:9001 --worker_hosts=8.129.168.22:2224,176.122.128.190:2225 --job_name=worker --task_index=1
