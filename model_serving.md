# Inference Servers / Deployment

## Personal Notes on Deployment

### 🤗 Hugging Face Inference Endpoints  
Docs: [HF Inference Endpoints](https://huggingface.co/docs/inference-endpoints/index)

#### Steps to Deploy:
1. Add billing information to your Hugging Face account.
2. Click **“Create new endpoint.”**
3. Select a model:
   - Use a pre-optimized model, or  
   - Select one from your own HF repository.
4. Choose a cloud provider (e.g., AWS, Azure).
5. Select an instance type (GPU recommended).
6. Set access permissions: public, SSL, or token-based.
7. Enable autoscaling:
   - Define thresholds to automatically spin up additional instances.
8. Configure environment settings:
   - Quantization, max tokens, batch size, etc.
9. Add tags, secrets, and metadata as needed.
10. Launch the endpoint.

#### Access Your Endpoint:
- [Test GUI](https://huggingface.co/docs/inference-endpoints/guides/test_endpoint)  
- API: cURL / REST

---

📝 **Notes:**  
Super easy to set up — only took a few minutes.
