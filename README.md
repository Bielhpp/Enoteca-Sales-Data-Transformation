# Enoteca Sales Data Transformation
This project focuses on the transformation of raw sales data from a wine shop, extracted from the [Bling](https://www.bling.com.br) sales control platform. The extracted data is disorganized and requires cleaning and formatting before being used for analysis or other purposes. In this repository, you will find the code used for data transformation using the Python programming language and the Apache Spark library.

## Requirements
Before running the code in this project, you need to have the following tools and libraries installed:
- [Apache Spark](https://spark.apache.org/)
- [Pandas](https://pandas.pydata.org/)
- [Jupyter Notebook](https://jupyter.org/)
Make sure all dependencies are installed before proceeding.

## Data Transformation
### Data Reading
Firstly, it is necessary to read the raw data that was extracted from the Bling platform.

### Cleaning and Formatting
Cleaning and formatting the data involve several steps:
- **Removal of unnecessary rows**
- **Filling null values in the "Cliente" column**
- **Conversion of numbers from strings to decimals**
- **Removal of unwanted columns**

### Data Visualization
If necessary, you can display the resulting DataFrame using Pandas.

### Data Export
To facilitate handling in other tools, the transformed data is exported to a CSV file.

## Usage
You can use the transformed data for analysis, reporting, or any other desired purpose.

## Contributions
Contributions are welcome! If you find ways to improve the code or identify issues, feel free to create an issue or send a pull request.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

This README provides an overview of the project, the data transformation steps, and the necessary requirements. Make sure to adapt it to your project and add any additional relevant information.
