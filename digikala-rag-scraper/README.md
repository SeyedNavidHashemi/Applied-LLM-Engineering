# Digikala Data Extractor for RAG Systems

This project contains scripts to automatically extract product data (specifically mobile phones) from the Digikala API. The extracted data is intended to serve as a knowledge base for a RAG (Retrieval-Augmented Generation) system.

## Key Features

* **Comprehensive ID Extraction:** Retrieves product IDs in the mobile phone category by automatically paginating through the Digikala API (e.g., 198 pages).
* **Safe & Incremental Saving:** Appends new IDs after processing each page and saves them to `product_ids.json`. This prevents data loss in case of network issues or unexpected interruptions (such as a `400 Bad Request` error).
* **Detailed Data Retrieval:** Processes the extracted list of IDs (e.g., 1963 unique products) and fetches the detailed information for each product individually.

## Prerequisites

To run this code, you need the following Python packages. In this project, dependencies are managed using `uv`:

```bash
uv add requests tqdm
```

## Directory Structure & Outputs

* **`digikala_data/` directory:** Created automatically by the script if it doesn't exist. All output files are stored here.
* **`product_ids.json`:** Contains the sorted and deduplicated list of extracted product IDs.
* **Product Data Files:** After running the second phase, detailed information for each product is saved as individual files named after their respective ID (e.g., `3992` or `4637`).
(You can access the raw data, embeddings and markdowns here -> [Dataset](https://huggingface.co/datasets/NavHash/digikala-mobile-expert-data))

## How It Works

1. The script initializes a `Session` with a specific `User-Agent` and sends requests to the endpoint:
   `api.digikala.com/v1/categories/mobile-phone/search`.
2. It identifies the total number of pages and products, then iteratively paginates through the results.
3. Whether the process completes successfully or gets interrupted, the extracted product IDs are safely saved.
4. In the second phase, the system loops through the unique IDs to download and save the detailed metadata for each product, readying the dataset for Vector DB ingestion.
5. The extracted product data is then processed and converted into embeddings, which are stored in a Vector Database to build the core retrieval engine of the RAG system.
6. A User Interface (UI) is included to seamlessly interact with, query, and test the capabilities of the final RAG system.
