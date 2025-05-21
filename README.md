
# QTM 350 - Data Science Computing

## Quiz 02: Creating a Website with Quarto and GitHub Pages

### Instructions

In this quiz, you will create a website using Quarto and GitHub Pages as shown in our previous lectures. The website will contain four pages:

- An index (home) page with a title, one sentence about the Gapminder dataset, and links to the other three pages.
- A page with a graph showing the relationship between life expectancy and GDP per capita over time.
- A page analysing the relationship between life expectancy and population.
- A page analysing changes in life expectancy, GDP per capita, and population for a specific country over time.

The website should be published on GitHub Pages and the link to the website should be submitted on Canvas. You can use either R or Python to create the graphs and the analysis. A short description of the dataset is provided here: <https://cran.r-project.org/web/packages/gapminder/index.html>.

The dataset is available in this repository as `gapminder.csv`, and it contains 6 columns and 1,704 rows. The columns are: `country`, `continent`, `year`, `life_expectancy`, `population_millions`, and `gdp_per_capita`. The dataset contains information about these variables in 142 countries over the years 1952 to 2007, with a 5-year interval. If you would like to create the dataset yourself, you can run the code below.

```python
# Install packages
# !pip install pandas gapminder

# Import necessary libraries
import pandas as pd
from gapminder import gapminder

# Rename 'lifeExp' to 'life_expectancy' and 'gdpPercap' to 'gdp_per_capita'
gapminder = gapminder.rename(columns={'lifeExp': 'life_expectancy',
                                      'pop': 'population_millions', 
                                      'gdpPercap': 'gdp_per_capita'})

# Convert population to millions
gapminder['population_millions'] = gapminder['population_millions'] / 1_000_000

# Create a new pandas DataFrame from the modified gapminder data
gapminder_df = pd.DataFrame(gapminder)

# Save the DataFrame as a CSV file
gapminder_df.to_csv('gapminder.csv', index=False)
```

### Tasks

1. Fork this repository to your GitHub account and clone it to your computer.

2. Create a new Quarto website project in your local cloned folder (use `.` if asked to choose your directory).

3. In your local folder, create another folder named `docs` to store the rendered website. This is the folder that will be published on GitHub Pages.

4. Modify the `_quarto.yml` file to include navigation links to your pages and direct the output to the `docs` folder.

5. Modify the `index.qmd` file to include a title, a one-line description of the Gapminder dataset, and links to the other website pages.

6. Create a page entitled `life-gdp.qmd` analysing the relationship between life expectancy and GDP per capita. Give it a title, a brief introduction, and a graph. Show your code. Also give it a link in the index page with the text "Life Expectancy and GDP per Capita".

7. Create a page entitled `life-population.qmd` analysing the relationship between life expectancy and population. Do the same as in the previous task, but change the title and the link text to "Life Expectancy and Population".

8. Create a page entitled `country.qmd` analysing changes in life expectancy, GDP per capita, and population for a specific country over time. Give it a title, a brief introduction, and a graph. Show your code. Also give it a link in the index page with the text "Country Analysis".

9. Ensure the `_quarto.yml` file includes navigation links with custom names.

10. Change the theme of the website to one of Quarto's available themes. You can find the list of themes here: <https://quarto.org/docs/output-formats/html-themes.html>.

11. Render the website and output the files to the `docs` folder.

12. Add, commit, and push the changes to your forked repository.

13. Go the repository settings on GitHub and enable GitHub Pages to publish the website. Remember to select the `docs` folder as the source.

14. Check that the website is live and all pages are accessible.

15. Copy the GitHub Pages link and submit it on Canvas as instructed.

### Bonus Question

16. Enhance the website's appearance by adding a custom CSS file.

17. Include an interactive map showing countries' life expectancy or GDP per capita. For this task, you can use the `plotly` library in Python, the `leaflet` library in R, or any other library you prefer.
=======
# QTM 350 - Quiz 03

## AI-Assisted Programming, Local LLMs, and Cloud Computing

In this quiz, you will need to complete two activities. The first involves creating a custom language model using [Ollama](https://ollama.com/). The second involves simple data analysis in Python using [AWS EC2](https://aws.amazon.com/ec2/). Both tasks relate to content covered in lectures 11, 13, 14, and 15.

As we have done in previous quizzes, answers must be in a fork of the quiz repository, whose link you should submit on Canvas.

**Screenshots will not be accepted.** Files and directories uploaded via the GitHub website (without using the terminal) will have points deducted.

## Activity 1: Creating a Custom Language Model with Ollama

In this first part of the quiz, you will create a chatbot called `sarcastic` that responds to user questions with sarcasm. The chatbot should be:

- Extremely sarcastic
- Subtly rude
- Reluctantly helpful
- Use sophisticated vocabulary and grammar
- Not overly verbose
- Capable of handling a wide range of topics
- Able to recognise and respond to sarcasm in user input

1. Fork this repository and clone your fork to your local machine
2. Create a directory called `ollama`. Inside the `ollama` directory, create a file called `Modelfile` and another called `ollama.md`
3. Install a base Ollama model. You may use any base model, but `gemma3`, `deepseek-r1` and `llama3.2` are recommended. **Pay attention to model sizes and choose a version suitable for your computer**. Use the smallest version available if in doubt. See available models at <https://ollama.com/models>
4. Create a Modelfile containing:
   - `FROM` statement
   - `PARAMETER` (at minimum `temperature`)
   - A detailed `SYSTEM` prompt describing the chatbot's personality and behaviour
5. Create the chatbot using the `Modelfile`
6. Test the chatbot using `ollama run sarcastic`. Verify it handles various topics with appropriate sarcasm
7. In `ollama.md`, document:
   - Commands used in the process
   - Two example prompts with the model's responses
8. Add, commit, and push your changes to your forked repository

## Activity 2: Data Analysis with Python on AWS EC2

In this second part, you will use AWS EC2 to perform simple Python data analysis. The script `weather_analysis.py`  analyses `weather_data.txt` (a fictional city's weather dataset). Both are available in the `aws` directory of this repository. The script:

- Calculates basic statistics
- Creates a visualisation showing temperature ranges and precipitation over time
- Saves the plot as `weather_analysis.png`

1. Log into your AWS account and create an EC2 instance with:
   - Ubuntu Server 24.04 LTS
   - SSD Volume Type
   - t2.micro instance type (free tier eligible)
2. Create an SSH key pair (`.pem`) or use an existing one. Ensure the key pair has the correct permissions with `chmod`
3. Configure security groups to allow SSH access
4. Allocate at least 10GB disk space (but less than 30GB) for the instance
5. Connect to the instance using `ssh -i <key.pem> ubuntu@<public-ip>`
6. Update and upgrade system packages with `apt`
7. Install required packages: `python3` `python3-pandas`, `python3-matplotlib`, `python3-numpy`, and `python3-seaborn`
8. From your local terminal, upload the files `weather_data.py` and `weather_data.txt` to the EC2 instance using `scp -i <key.pem> <file> ubuntu@<public-ip>:~` (note that the `:~` specifies the home directory of your instance)
9. Run the script `weather_analysis.py` on the EC2 instance using Python
10. Run the command `cat /etc/os-release > os.txt` on the instance
11. From your local terminal, download the `os.txt` and `weather_analysis.png` files to the `aws` directory on your machine (note the syntax: `scp -i <key.pem> <source> <destination>`)
12. **Terminate the EC2 instance** to avoid charges and **do not include the .pem file in your repository**. The `.pem` file is sensitive and should never be shared publicly
13. Add, commit, and push your changes
14. Submit your repository link on Canvas

**Good luck!** 😃
>>>>>>> quiz03/main
