This function performs two main tasks:


*   **Captions Generation & Saving:**
It first processes the video frame-by-frame to generate captions for each frame using a pre-trained image captioning model. For every frame, it saves the corresponding captions in a text file, along with their associated timestamps. The timestamps mark when each captioned event occurs in the video (e.g., "a man talking on a phone: 10 sec").

*   **Query Matching & Video Extraction:**
After generating the captions, the function uses a similarity model (specifically, the SentenceTransformer('all-MiniLM-L6-v2') model) to compare the query you provide (e.g., "man talking on phone") with the generated captions.
It doesn't need an exact match! Instead, it calculates the semantic similarity between the query and each caption. Captions that are sufficiently similar are selected.
Once it identifies the relevant captions, the function looks at the timestamps associated with those captions and extracts the segment of the video that corresponds to those time points.
For example: If your query is "man talking on phone" and the captions at 10, 11, and 12 seconds all mention a man talking on a phone, the function will extract the video from 10 to 12 seconds, giving you just that portion of the video.
