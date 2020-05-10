git clone https://github.com/mxito3/distributeTensorflowExample && cd distributeTensorflowExample

apt install software-properties-common && add-apt-repository ppa:deadsnakes/ppa && apt update && apt install python3.7 &&  apt install python3.7-dev && apt install python3.7-venv

python3.7 -m venv venv && source venv/bin/activate && pip install -r requirements.txt

ps 节点执行： 


 cd distributeTensorflowExample && python3.7 -m venv venv && source venv/bin/activate  && CUDA_VISIBLE_DEVICES='' python trainer.py --ps_hosts=47.75.243.164:9001 --worker_hosts=8.129.168.22:30304,176.122.128.190:2225 --job_name=ps --task_index=0



worker 节点执行:

 cd distributeTensorflowExample && python3.7 -m venv venv && source venv/bin/activate  && python trainer.py --ps_hosts=47.75.243.164:9001 --worker_hosts=8.129.168.22:30304,176.122.128.190:2225 --job_name=worker --task_index=0

 cd distributeTensorflowExample && python3.7 -m venv venv && source venv/bin/activate  && CUDA_VISIBLE_DEVICES=0 python trainer.py --ps_hosts=47.75.243.164:9001 --worker_hosts=8.129.168.22:30304,176.122.128.190:2225 --job_name=worker --task_index=1
