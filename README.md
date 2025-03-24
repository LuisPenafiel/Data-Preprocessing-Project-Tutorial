# Exploratory Data Analysis Project

This project serves as a template for machine learning projects, demonstrating best practices in data collection, exploration, cleaning, and preprocessing, as well as feature selection. It uses the Airbnb NYC 2019 dataset (AB_NYC_2019.csv) to illustrate these processes, preparing the data for a machine learning model that could predict the price of listings (although model training is not included in this code).

## Project Structure

The project is organized as follows:

.
├── data
│   ├── raw
│   │   └── total_data.csv          
│   └── processed
│       ├── clean_train.csv         
│       └── clean_test.csv          
├── notebooks
│   └── project_notebook.ipynb      
├── requirements.txt                
└── README.md                       

- `data/raw/`: Contains the unprocessed dataset (`total_data.csv`), downloaded directly from the source.
- `data/processed/`: Stores the cleaned and processed data, split into training (`clean_train.csv`) and test (`clean_test.csv`) sets.
- `notebooks/`: Includes the Jupyter notebook (`project_notebook.ipynb`) with the complete preprocessing workflow.
- `requirements.txt`: Lists the Python dependencies required to run the project.

## Installation

Follow these steps to set up the project environment:

1. **Clone the repository**:
   git clone https://github.com/your_user/your_repository.git

2. **Navigate to the project directory**:
   cd your_repository

3. **Install the dependencies**:
   Ensure you have Python installed (recommended version: 3.8 or higher) and run:
   pip install -r requirements.txt
   Note: The `requirements.txt` file must include at least the following libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`. Example content:
   pandas>=1.5.3
   numpy>=1.24.3
   matplotlib>=3.7.1
   seaborn>=0.12.2
   scikit-learn>=1.0.0
   requests>=2.28.0

4. **Verify the installation**:
   If you encounter errors related to paths or missing dependencies, install the required libraries manually, for example:
   pip install seaborn


## Usage

The main workflow of the project is contained in the notebook `notebooks/project_notebook.ipynb`. To run it:

1. **Start Jupyter Notebook**:
   From the project's root directory, run:
   jupyter notebook

2. **Open the notebook**:
   In the browser, select `project_notebook.ipynb` and execute the cells sequentially.

The notebook includes the following steps:
- **Data Collection**: Downloads the Airbnb NYC 2019 dataset.
- **Exploration**: Basic analysis of the variables.
- **Cleaning**: Handling of missing values and removal of duplicates.
- **Outlier Detection**: Identification and filtering of outliers.
- **Feature Scaling**: Normalization of numerical variables.
- **Feature Selection**: Identification of the most relevant features.
- **Saving**: Exporting the processed data.

## Data

The project uses the **Airbnb NYC 2019** dataset, which contains information about Airbnb listings in New York. This dataset is downloaded from:
https://raw.githubusercontent.com/4GeeksAcademy/data-preprocessing-project-tutorial/main/AB_NYC_2019.csv

### Dataset Columns
- `id`: Listing identifier
- `name`: Listing name
- `host_id`: Host identifier
- `host_name`: Host name
- `neighbourhood_group`: Borough (e.g., Brooklyn, Manhattan)
- `neighbourhood`: Specific neighborhood
- `latitude`: Latitude
- `longitude`: Longitude
- `room_type`: Room type (e.g., Private room, Entire home/apt)
- `price`: Price per night (implicit target variable)
- `minimum_nights`: Minimum nights of stay
- `number_of_reviews`: Number of reviews
- `last_review`: Date of the last review
- `reviews_per_month`: Reviews per month
- `calculated_host_listings_count`: Number of listings by the host
- `availability_365`: Days available per year

The raw data is saved in `data/raw/total_data.csv`.

## Data Preprocessing

The preprocessing includes the following steps detailed in the notebook:

1. **Data Cleaning**:
   - Removal of duplicates.
   - Handling of missing values (although a specific method is not detailed in the code, imputation or removal is suggested depending on the case).

2. **Outlier Detection and Handling**:
   - For `number_of_reviews`: The interquartile range (IQR) is calculated to identify outliers.
   - For `calculated_host_listings_count`: Listings with more than 4 properties per host are filtered out.

3. **Feature Scaling**:
   - The `MinMaxScaler` from scikit-learn is applied to numerical variables such as `number_of_reviews`, `minimum_nights`, `calculated_host_listings_count`, and `availability_365`, as well as to encoded categorical variables like `neighbourhood_group` and `room_type`.

4. **Feature Selection**:
   - The `SelectKBest` method with the `chi2` metric is used to select the 4 most relevant features in relation to the price (`price`). The selected features include `number_of_reviews`, `minimum_nights`, `calculated_host_listings_count`, and `room_type`.

5. **Data Splitting**:
   - The processed data is split into training (80%) and test (20%) sets using `train_test_split` with a random seed (`random_state = 42`).

6. **Saving**:
   - The processed data is exported to `data/processed/clean_train.csv` and `data/processed/clean_test.csv`.

## Feature Engineering

- **Encoding of Categorical Variables**: Although not explicitly shown in the code, it is inferred that `neighbourhood_group` and `room_type` are encoded (e.g., using one-hot encoding or label encoding) before scaling.
- **Transformation**: Numerical variables are scaled to the range [0, 1] to improve performance in future models.

## Model Training

This project does not include the training of a machine learning model, but the processed data is ready to be used in prediction algorithms (e.g., regression to predict `price`). You can extend the notebook by adding this section.

## Results

Since the focus is on preprocessing, no performance metrics are presented. However, the pipeline ensures that the data is clean, scaled, and optimized for modeling.

## Contributions

Contributions are welcome! To collaborate:

1. Fork the repository.
2. Create a branch with your changes (`git checkout -b feature/new-functionality`).
3. Submit a pull request with a clear description of your changes.

## License

This project is licensed under the **MIT License**.