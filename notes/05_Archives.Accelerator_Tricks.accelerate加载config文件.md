---
id: g1vonkyzj3ibrzt8wur5o3y
title: accelerate加载config文件
desc: ''
updated: 1703825402189
created: 1703825288650
---

使用accelerate训练模型的时候，不需要执行accelerate config命令配置众多参数，而是直接写入参数到yaml文件，然后使用--config 进行读取：

完整的bash代码如下：

```bash



gpu_ids=$1
teacher_name=$2
domain_class_token=$3

# YAML配置内容
config="compute_environment: LOCAL_MACHINE
debug: false
distributed_type: 'NO'
downcast_bf16: 'no'
gpu_ids: '$gpu_ids'
machine_rank: 0
main_training_function: main
mixed_precision: 'no'
num_machines: 1
num_processes: 1
rdzv_backend: static
same_network: true
tpu_env: []
tpu_use_cluster: false
tpu_use_sudo: false
use_cpu: false"

# 将配置内容写入到文件中
echo "$config" > ./accelerate_config/config_$teacher_name.yaml

echo "配置已写入到 config_$teacher_name.yaml 文件中，gpu_ids 参数为: $gpu_ids"



CUDA_VISIBLE_DEVICES=1 accelerate  launch --config_file ./accelerate_config/config_$teacher_name.yaml  --main_process_port 29531 pretrain_inversion_student_appearance_img_generation_new_kv.py \
  --checkpointing_steps=10 \
  --clip_model_name_or_path="ViT-B-32::/home/wangye/huggingface_ckpts/CLIP-ViT-B-32-laion2B-s34B-b79K/open_clip_pytorch_model.bin" \
  --dataset_class="dog" \
  --domain_class_token=$domain_class_token \
  --shape_class_token="shape" \
  --appearance_class_token="appearance" \
  --domain_embed_scale=0.1 \
  --exp_name="Appearance_Inversion" \
  --exp_desc="Teacher-Student-Architecture-V2" \
  --iterable_dataset \
  --learning_rate=1e-5 --scale_lr \
  --log_steps=20 \
  --max_train_steps=3000 \
  --mixed_precision="fp16" \
  --output_dir="/home/wangye/Research2023/ShapeInversion_Exp/Appearance_Inversion_Cases/appearance-$teacher_name-appearance-encoder-upblock" \
  --placeholder_token="*s" \
  --placeholder_token_shape="*m" \
  --placeholder_token_appearance="*a" \
  --pretrained_model_name_or_path="/home/wangye/huggingface_ckpts/stable-diffusion-v1-4" \
  --prompt_template="joint" \
  --reg_lambda=0.01 \
  --resolution=512 \
  --student_prompt="a $domain_class_token in the appearance of *a" \
  --train_batch_size=1 \
  --origin_img_path="/home/wangye/Research2023/ShapeInversion/test_data/appearance/imgs_1/$teacher_name.png" \
  --mask_img_path="/home/wangye/Research2023/ShapeInversion/test_data/appearance/masks_1/$teacher_name.pkl" \
  --gradient_accumulation_steps=2 \
  --loss_diff_student_weight=1.0 \
  --loss_shape_weight=0.0 \
  --loss_appearance_weight=0.0 \
  --temp_dino_or_e4t="e4t" \
  --unfreeze_clip_vision \
  --is_need_augment \
  --use_8bit_adam

```

由上述代码为例，gpu_ids是我每次需要传入的gpu编号。


