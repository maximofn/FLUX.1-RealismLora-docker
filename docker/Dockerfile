FROM nvcr.io/nvidia/cuda:11.8.0-cudnn8-devel-ubuntu22.04

RUN apt-get update \
    && apt-get install -y --no-install-recommends git git-lfs python3 python3-pip \
    && apt-get install -y --no-install-recommends libgl1-mesa-glx libglib2.0-0 \
    && curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | bash \
    && git lfs install \
    && rm cuda-keyring_1.0-1_all.deb \
    && ln -s /usr/bin/python3 /usr/bin/python \
    && rm -rf /var/lib/apt/lists/*

RUN pip3 install --no-cache-dir torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

RUN git clone --depth 1 https://huggingface.co/spaces/DamarJati/FLUX.1-RealismLora \
    && cd FLUX.1-RealismLora && pip3 install --no-cache-dir -r requirements.txt

RUN pip3 install --no-cache-dir gradio protobuf

RUN sed -i 's/base_model = "black-forest-labs\/FLUX.1-dev"/base_model = "Freepik\/flux.1-lite-8B-alpha"/g' /FLUX.1-RealismLora/app.py \
    && ls \
    && sed -i 's/pipe = DiffusionPipeline.from_pretrained(base_model, torch_dtype=torch.bfloat16)/pipe = DiffusionPipeline.from_pretrained(base_model, torch_dtype=torch.bfloat16, device_map="balanced")/g' /FLUX.1-RealismLora/app.py \
    && sed -i 's/pipe.to("cuda")/# pipe.to("cuda")/g' /FLUX.1-RealismLora/app.py

WORKDIR /FLUX.1-RealismLora