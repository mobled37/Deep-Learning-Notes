**Problem**: Existing text-video retrieval solutions overlook the underlying data distribution $p$ (query), which makes it challenging to identify out-of-distribution data. 
**Solution**: Diffusion-based Text-video Retrieval framework (DiffusionRet), which models the retrieval task as a process of gradually generating joint distribution from noise.

**Advantages**:
1. Generative paradigm -> inherently **generalizable** and **transferrable** -> enabling DiffusionRet to adapt to out-of-domain samples without requiring additional design. 
2. **Iterative refinement property** of diffusion model -> enabling DiffusionRet to progressively enhance the retrieval results from coarse to fine. 

**Datasets**: MSRVTT, LSMDC, MSVD, ActivityNet Captions, DiDeMo