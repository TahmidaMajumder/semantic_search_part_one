# YouTube Video ETL Pipeline & Semantic Search

A comprehensive ETL pipeline for extracting YouTube video data, transforming it, and building semantic search capabilities with machine learning models.

## Project Overview

This project consists of two main components:
1. **ETL Pipeline** - Extract YouTube video metadata and transcripts, then transform the data
2. **Machine Learning Solution** - Compare semantic search models, create embeddings, and build a Gradio web application

The pipeline extracts video titles and transcripts from YouTube channels, processes the data, and creates a semantic search system to find relevant videos based on content similarity.

<h2 align="center">📺 Demo Video</h2>

<p align="center">
  <a href="https://www.youtube.com/watch?v=dLFiNk6YksA" target="_blank">
    <img src="https://img.youtube.com/vi/dLFiNk6YksA/0.jpg" alt="Watch the demo" />
  </a>
</p>

## Project Structure

```
semantic_search_part_one/
├── ETL/
│   ├── Extract_Data_Part_1.ipynb     # Extract video metadata from YouTube API
│   ├── Extract_Data_Part_2.ipynb     # Extract video transcripts
│   ├── Transform_Data.ipynb          # Data transformation and analysis
│   ├── my_sk.py                      # API keys (not included in repo)
│   ├── data/
│   │   ├── video-ids.csv/parquet     # Video metadata
│   │   └── video-transcripts.csv/parquet  # Video data with transcripts
│   └── requirements.txt
├── Machine Learning Solution/
│   ├── 4. Compare_Models.ipynb       # Model comparison and evaluation
│   ├── 5. Embedding.ipynb           # Data embedding process
│   ├── 6. Semantic_Search.ipynb     # Semantic search implementation
│   ├── data/
│   │   ├── video-ids.csv/parquet
│   │   ├── video-transcripts.csv/parquet
│   │   ├── video_index.parquet
│   │   └── eval_data/               # Evaluation datasets
│   └── requirements.txt
└── README.md
```

## Features

### ETL Pipeline
- **Extract Video Metadata**: Fetch video IDs, titles, and publication dates from YouTube channels
- **Extract Transcripts**: Download video transcripts using YouTube Transcript API
- **Data Transformation**: Clean and analyze the extracted data, including:
  - Data quality assessment and statistics
  - DateTime format conversion
  - HTML entity cleaning and text preprocessing
  - Data visualization and distribution analysis
- **Multiple Output Formats**: Save data in both CSV and Parquet formats

### Machine Learning Solution
- **Model Comparison**: Compare multiple semantic search models with comprehensive evaluation
  - 3 SentenceTransformer models tested
  - 5 distance/similarity metrics compared
  - 45 total model-metric combinations evaluated
- **Distance & Similarity Metrics**: Evaluate model performance using various metrics
- **Data Embedding**: Create vector embeddings for semantic search using best performing model
- **Gradio Web App**: Interactive web interface for semantic search with:
  - Real-time search functionality
  - Threshold-based filtering
  - Top-k results display
  - Embedded YouTube video previews
  - Direct video links

## Installation

1. **Clone the repository**:
```bash
git clone https://github.com/yourusername/semantic_search_part_one.git
cd semantic_search_part_one
```

2. **Set up Python environment**:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install ETL dependencies**:
```bash
cd ETL
pip install -r requirements.txt
```

4. **Install ML dependencies**:
```bash
cd ../Machine\ Learning\ Solution
pip install -r requirements.txt
```

5. **Set up API keys**:
   - Create a `my_sk.py` file in the ETL folder
   - Add your YouTube API key: `my_sk = "your_youtube_api_key_here"`

## Running the Application

### Complete Pipeline Execution

1. **Set up environment and API keys**:
   ```bash
   # Create my_sk.py in ETL folder
   echo "my_sk = 'your_youtube_api_key'" > ETL/my_sk.py
   ```

2. **Run ETL Pipeline**:
   ```bash
   cd ETL
   jupyter notebook Extract_Data_Part_1.ipynb  # Extract video metadata
   jupyter notebook Extract_Data_Part_2.ipynb  # Extract transcripts
   jupyter notebook Transform_Data.ipynb       # Clean and transform data
   ```

3. **Run ML Pipeline**:
   ```bash
   cd "../Machine Learning Solution"
   jupyter notebook "4. Compare_Models.ipynb"  # Compare models
   jupyter notebook "5. Embedding.ipynb"       # Generate embeddings
   jupyter notebook "6. Semantic_Search.ipynb" # Launch Gradio app
   ```

4. **Access the Web App**:
   - The Gradio interface will launch automatically
   - Search for videos using natural language queries
   - Results include embedded YouTube videos and direct links

## Tools & Technologies

- **Data Processing**: Polars, Pandas
- **APIs**: YouTube Data API v3, YouTube Transcript API
- **Machine Learning**: Scikit-learn, Transformers, Sentence-Transformers, PyTorch
- **Web Framework**: Gradio
- **Data Storage**: Parquet, CSV
- **Visualization**: Matplotlib
- **Environment**: Jupyter Notebooks

## Requirements

### ETL Pipeline
- requests
- polars
- youtube-transcript-api
- matplotlib
- textwrap
- re

### Machine Learning Solution
- sentence-transformers
- torch
- scikit-learn
- numpy
- matplotlib
- gradio
- polars (LazyFrame for efficient data handling)

## Data Flow

1. **Extraction**: YouTube API → Video metadata → Transcript API → Full dataset
2. **Transformation**: 
   - Data quality analysis (shape, unique values, character counts)
   - DateTime format conversion
   - HTML entity cleaning and text preprocessing
   - Data visualization and statistical analysis
   - Cleaned data export
3. **ML Processing**: 
   - Comprehensive model comparison (3 models × 3 text sources × 5 metrics = 45 combinations)
   - Best performing model selection (all-MiniLM-L6-v2 with Manhattan distance)
   - Embedding generation for titles and transcripts
   - Video index creation with vector embeddings
   - Semantic search implementation with threshold filtering
4. **Application**: Gradio web interface with embedded YouTube videos and real-time search

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the under theApache-2.0 license. See the LICENSE file for details.

## Notes

- Ensure you have a valid YouTube Data API key before running the extraction scripts
- The `my_sk.py` file containing API keys is not included in the repository for security reasons
- Large datasets may take significant time to process, especially transcript extraction
- Monitor API usage limits when extracting data from YouTube

## Next Steps

- Complete machine learning model implementation
- Add more sophisticated data preprocessing
- Implement advanced semantic search algorithms
- Deploy the Gradio application
- Add comprehensive error handling and logging
