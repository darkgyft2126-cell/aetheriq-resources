# Build of the Week — Edition 10: Run a Ready-Trained MiniMind Model

Goal: run the ready-trained MiniMind-3 model on your own machine and test it with questions you can check by hand. Inference only — no training. Budget: under one hour.

Source repo: https://github.com/jingyaogong/minimind (Apache-2.0). Commands below are from the repo README, read on Nov 24, 2026.

## Steps

1. Clone the repo and install its requirements:

   ```
   git clone --depth 1 https://github.com/jingyaogong/minimind
   cd minimind
   pip install -r requirements.txt
   ```

2. Download the ready-trained weights (pick one):

   ```
   # Option A — ModelScope
   modelscope download --model gongjy/minimind-3 --local_dir ./minimind-3

   # Option B — Hugging Face
   git clone https://huggingface.co/jingyaogong/minimind-3
   ```

3. Run the model from the project root:

   ```
   python eval_llm.py --load_from ./minimind-3
   ```

4. Test it like a buyer, not a fan. Ask three questions whose answers you know cold: one fact, one short sum, one instruction with two parts. Write down which it gets right and where it fails. A 64M model is a teaching model — the failures are the lesson.

5. Optional, if you finish early: start the chat WebUI. Copy the model folder into `scripts/` first, then:

   ```
   pip install streamlit
   cd scripts && streamlit run web_demo.py
   ```

## Notes

- The repo's full training path (pretrain plus fine-tune) takes about two hours on one RTX 3090 per the README. That path is out of scope for this one-hour build; this quickstart runs the finished weights only.
- MiniMind also runs through Ollama: `ollama run jingyaogong/minimind-3`.
- If CUDA is not available, the repo notes CPU or MPS can run, but much slower. For three test questions, CPU is still enough to finish inside the hour.
