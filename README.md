{
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/Kenkimmax/dsc-phase-1-project-v2-4/blob/master/README.md\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "Ol4OoA8sigvt"
      },
      "source": [
        "## Final Project Submission\n",
        "\n",
        "Please fill out:\n",
        "* Student name: Kenneth Kimani\n",
        "* Student pace: self paced / part time / full time\n",
        "* Scheduled project review date/time: \n",
        "* Instructor name: \n",
        "* Blog post URL:\n"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "iLDHpD26igv6"
      },
      "outputs": [],
      "source": [
        "# Your code here - remember to use markdown cells for comments as well!"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Microsoft Movie Production Need Analysis"
      ],
      "metadata": {
        "id": "xwRpCO9B_OJt"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "OVERVIEW\n",
        "The project analyzes was to provide actionable insight to the Microsoft Head of new movie Studio. The analysis used data from 3 sources namely: Movie_info, reviews and bom movie.\n",
        "\n",
        "Key Takeouts:\n",
        "Top 5 movie genre to produce fall under the five big catergorirs Action and Adventure|Classics|Drama, Drama|Science Fiction and Fantasy,Drama|Musical and Performing Arts, Drama|Mystery and Suspense and Drama|Kids and Family' 'Comedy\n",
        "\n",
        "The optimal Movie duration is critical to the Audience.\n",
        "\n",
        "Understading the different season patterns to release new movies.\n",
        "\n",
        "Speak into the production cost.\n",
        "\n",
        "\n"
      ],
      "metadata": {
        "id": "r-cN4frS_rh2"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "Business Problem\n",
        "\n",
        "Microsoft sees all the big companies creating original video content and they want to get in on the fun. They have decided to create a new movie studio, but they don’t know anything about creating movies. You are charged with exploring what types of films are currently doing the best at the box office. You must then translate those findings into actionable insights that the head of Microsoft's new movie studio can use to help decide what type of films to create."
      ],
      "metadata": {
        "id": "Z_MAdz0aDu-7"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "Data Understanding\n",
        "\n",
        "The Movie_info data source contains movie details from 1921 to 2018.The data entails movie theater release dates, the writer, director and the movie rating categories.\n",
        "\n",
        "The Movie budget data source contains the name, release date, the production costs and both the domestic and foreign earnings from 2014 t0 2020.\n",
        "\n",
        "The bom movie data source has the movie title,studio,domestic and foreign earunings and release year.The data runs from 2010 to 2020."
      ],
      "metadata": {
        "id": "etV4u0e2D_Hh"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "Import Data from the CSV files.We first import the needed libraries.\n"
      ],
      "metadata": {
        "id": "e4NcV3epnReS"
      }
    },
    {
      "cell_type": "markdown",
      "source": [],
      "metadata": {
        "id": "73NKHTE8n8Xw"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "#import the needed libraries.\n",
        "import pandas as pd\n",
        "import numpy as np\n",
        "import matplotlib.pyplot as plt\n",
        "import seaborn as sns\n"
      ],
      "metadata": {
        "id": "3W0FCaiknsFN"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Load the movie_info into a DataFrame and Explore the data.\n",
        "The Movie_info data source contains movie details from 1921 t0 2018.The data entails movie theater relaese dates, the writer, director and the movie rating categories.\n"
      ],
      "metadata": {
        "id": "Sri0j6r8oleS"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "movie_information = pd.read_csv('/content/rt.movie_info.tsv', delimiter='\\t',index_col=0)\n",
        "movie_information.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 455
        },
        "id": "oaaRdN0SpB74",
        "outputId": "1e716157-4cd8-4e39-9dff-e3de97c39cf2"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                                             synopsis rating  \\\n",
              "id                                                             \n",
              "1   This gritty, fast-paced, and innovative police...      R   \n",
              "3   New York City, not-too-distant-future: Eric Pa...      R   \n",
              "5   Illeana Douglas delivers a superb performance ...      R   \n",
              "6   Michael Douglas runs afoul of a treacherous su...      R   \n",
              "7                                                 NaN     NR   \n",
              "\n",
              "                                  genre          director  \\\n",
              "id                                                          \n",
              "1   Action and Adventure|Classics|Drama  William Friedkin   \n",
              "3     Drama|Science Fiction and Fantasy  David Cronenberg   \n",
              "5     Drama|Musical and Performing Arts    Allison Anders   \n",
              "6            Drama|Mystery and Suspense    Barry Levinson   \n",
              "7                         Drama|Romance    Rodney Bennett   \n",
              "\n",
              "                             writer  theater_date      dvd_date currency  \\\n",
              "id                                                                         \n",
              "1                    Ernest Tidyman   Oct 9, 1971  Sep 25, 2001      NaN   \n",
              "3      David Cronenberg|Don DeLillo  Aug 17, 2012   Jan 1, 2013        $   \n",
              "5                    Allison Anders  Sep 13, 1996  Apr 18, 2000      NaN   \n",
              "6   Paul Attanasio|Michael Crichton   Dec 9, 1994  Aug 27, 1997      NaN   \n",
              "7                      Giles Cooper           NaN           NaN      NaN   \n",
              "\n",
              "   box_office      runtime             studio  \n",
              "id                                             \n",
              "1         NaN  104 minutes                NaN  \n",
              "3     600,000  108 minutes  Entertainment One  \n",
              "5         NaN  116 minutes                NaN  \n",
              "6         NaN  128 minutes                NaN  \n",
              "7         NaN  200 minutes                NaN  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-d1cdf0bd-d64b-408e-8c5c-7751a3034965\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>synopsis</th>\n",
              "      <th>rating</th>\n",
              "      <th>genre</th>\n",
              "      <th>director</th>\n",
              "      <th>writer</th>\n",
              "      <th>theater_date</th>\n",
              "      <th>dvd_date</th>\n",
              "      <th>currency</th>\n",
              "      <th>box_office</th>\n",
              "      <th>runtime</th>\n",
              "      <th>studio</th>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>id</th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>This gritty, fast-paced, and innovative police...</td>\n",
              "      <td>R</td>\n",
              "      <td>Action and Adventure|Classics|Drama</td>\n",
              "      <td>William Friedkin</td>\n",
              "      <td>Ernest Tidyman</td>\n",
              "      <td>Oct 9, 1971</td>\n",
              "      <td>Sep 25, 2001</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>104 minutes</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>New York City, not-too-distant-future: Eric Pa...</td>\n",
              "      <td>R</td>\n",
              "      <td>Drama|Science Fiction and Fantasy</td>\n",
              "      <td>David Cronenberg</td>\n",
              "      <td>David Cronenberg|Don DeLillo</td>\n",
              "      <td>Aug 17, 2012</td>\n",
              "      <td>Jan 1, 2013</td>\n",
              "      <td>$</td>\n",
              "      <td>600,000</td>\n",
              "      <td>108 minutes</td>\n",
              "      <td>Entertainment One</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>5</th>\n",
              "      <td>Illeana Douglas delivers a superb performance ...</td>\n",
              "      <td>R</td>\n",
              "      <td>Drama|Musical and Performing Arts</td>\n",
              "      <td>Allison Anders</td>\n",
              "      <td>Allison Anders</td>\n",
              "      <td>Sep 13, 1996</td>\n",
              "      <td>Apr 18, 2000</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>116 minutes</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>6</th>\n",
              "      <td>Michael Douglas runs afoul of a treacherous su...</td>\n",
              "      <td>R</td>\n",
              "      <td>Drama|Mystery and Suspense</td>\n",
              "      <td>Barry Levinson</td>\n",
              "      <td>Paul Attanasio|Michael Crichton</td>\n",
              "      <td>Dec 9, 1994</td>\n",
              "      <td>Aug 27, 1997</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>128 minutes</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>7</th>\n",
              "      <td>NaN</td>\n",
              "      <td>NR</td>\n",
              "      <td>Drama|Romance</td>\n",
              "      <td>Rodney Bennett</td>\n",
              "      <td>Giles Cooper</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>200 minutes</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-d1cdf0bd-d64b-408e-8c5c-7751a3034965')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-d1cdf0bd-d64b-408e-8c5c-7751a3034965 button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-d1cdf0bd-d64b-408e-8c5c-7751a3034965');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 3
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#movie_rating = movie_information.pivot(index='synopsis', columns='director', values='currency')\n",
        "#movie_rating.head()"
      ],
      "metadata": {
        "id": "7Ksp5vyOkIvx"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Conduct some data Exploratory data analysis."
      ],
      "metadata": {
        "id": "09P8bwxEioQw"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "movie_information.shape"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "cQ6IrgDIRAsY",
        "outputId": "bd41bf72-9eca-4b29-ec75-f63f8ee07434"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "(1560, 11)"
            ]
          },
          "metadata": {},
          "execution_count": 5
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "movie_information.describe()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 236
        },
        "id": "nnugIpggAwJW",
        "outputId": "fc8c075a-83bf-44e0-dfbf-f669c85bdd9d"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                                                 synopsis rating  genre  \\\n",
              "count                                                1498   1557   1552   \n",
              "unique                                               1497      6    299   \n",
              "top     A group of air crash survivors are stranded in...      R  Drama   \n",
              "freq                                                    2    521    151   \n",
              "\n",
              "                director       writer theater_date     dvd_date currency  \\\n",
              "count               1361         1111         1201         1201      340   \n",
              "unique              1125         1069         1025          717        1   \n",
              "top     Steven Spielberg  Woody Allen  Jan 1, 1987  Jun 1, 2004        $   \n",
              "freq                  10            4            8           11      340   \n",
              "\n",
              "       box_office     runtime              studio  \n",
              "count         340        1530                 494  \n",
              "unique        336         142                 200  \n",
              "top       600,000  90 minutes  Universal Pictures  \n",
              "freq            2          72                  35  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-31f66c4d-cea7-4108-8a77-06ff66b246e4\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>synopsis</th>\n",
              "      <th>rating</th>\n",
              "      <th>genre</th>\n",
              "      <th>director</th>\n",
              "      <th>writer</th>\n",
              "      <th>theater_date</th>\n",
              "      <th>dvd_date</th>\n",
              "      <th>currency</th>\n",
              "      <th>box_office</th>\n",
              "      <th>runtime</th>\n",
              "      <th>studio</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>count</th>\n",
              "      <td>1498</td>\n",
              "      <td>1557</td>\n",
              "      <td>1552</td>\n",
              "      <td>1361</td>\n",
              "      <td>1111</td>\n",
              "      <td>1201</td>\n",
              "      <td>1201</td>\n",
              "      <td>340</td>\n",
              "      <td>340</td>\n",
              "      <td>1530</td>\n",
              "      <td>494</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>unique</th>\n",
              "      <td>1497</td>\n",
              "      <td>6</td>\n",
              "      <td>299</td>\n",
              "      <td>1125</td>\n",
              "      <td>1069</td>\n",
              "      <td>1025</td>\n",
              "      <td>717</td>\n",
              "      <td>1</td>\n",
              "      <td>336</td>\n",
              "      <td>142</td>\n",
              "      <td>200</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>top</th>\n",
              "      <td>A group of air crash survivors are stranded in...</td>\n",
              "      <td>R</td>\n",
              "      <td>Drama</td>\n",
              "      <td>Steven Spielberg</td>\n",
              "      <td>Woody Allen</td>\n",
              "      <td>Jan 1, 1987</td>\n",
              "      <td>Jun 1, 2004</td>\n",
              "      <td>$</td>\n",
              "      <td>600,000</td>\n",
              "      <td>90 minutes</td>\n",
              "      <td>Universal Pictures</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>freq</th>\n",
              "      <td>2</td>\n",
              "      <td>521</td>\n",
              "      <td>151</td>\n",
              "      <td>10</td>\n",
              "      <td>4</td>\n",
              "      <td>8</td>\n",
              "      <td>11</td>\n",
              "      <td>340</td>\n",
              "      <td>2</td>\n",
              "      <td>72</td>\n",
              "      <td>35</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-31f66c4d-cea7-4108-8a77-06ff66b246e4')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-31f66c4d-cea7-4108-8a77-06ff66b246e4 button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-31f66c4d-cea7-4108-8a77-06ff66b246e4');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 6
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "movie_information.duplicated().value_counts()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "XfaMIDIblYUq",
        "outputId": "9a9b2f24-b4d9-420b-d5be-47e576eabcbf"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "False    1556\n",
              "True        4\n",
              "dtype: int64"
            ]
          },
          "metadata": {},
          "execution_count": 7
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "# Convert the theater_date to datetime\n",
        "movie_information['theater_date'] =  pd.to_datetime(movie_information['theater_date'])\n",
        "movie_information['theater_date'].describe()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "BdJeMaJim-Sq",
        "outputId": "48934fa9-a18d-4521-dc60-85e64e4a8477"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "<ipython-input-8-86242a280f5e>:2: FutureWarning: Treating datetime data as categorical rather than numeric in `.describe` is deprecated and will be removed in a future version of pandas. Specify `datetime_is_numeric=True` to silence this warning and adopt the future behavior now.\n",
            "  movie_information['theater_date'].describe()\n"
          ]
        },
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "count                    1201\n",
              "unique                   1025\n",
              "top       1987-01-01 00:00:00\n",
              "freq                        8\n",
              "first     1921-01-01 00:00:00\n",
              "last      2018-10-19 00:00:00\n",
              "Name: theater_date, dtype: object"
            ]
          },
          "metadata": {},
          "execution_count": 8
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Explore the Director column to understand the top talents."
      ],
      "metadata": {
        "id": "UBV-iIK0baqB"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "\n",
        "top_director = movie_information[\"director\"].unique()[:10]\n",
        "\n",
        "top_director_counts = movie_information[\"director\"].value_counts().nlargest(10).tolist()\n",
        "\n",
        "#print(\"Genre:\", top_genre)\n",
        "#print(\"Counts:\", top_genre_counts)\n",
        "\n",
        "#sns.barplot(data = movie_information, y = top_director_counts, x = top_director )\n",
        "\n",
        "y= top_director\n",
        " \n",
        "# getting values against each value of y\n",
        "x= top_director_counts\n",
        "plt.barh(y, x , color = 'blue' , alpha =0.75)\n",
        "\n",
        " \n",
        "# setting label of y-axis\n",
        "plt.ylabel(\"Count of movie Releases \")\n",
        " \n",
        "# setting label of x-axis\n",
        "plt.xlabel(\"Counts\")\n",
        "plt.title(\"Top 10 Active Movie Directors (No.Releases)\")\n",
        "plt.show()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 472
        },
        "id": "hyYwGOJ9q0iQ",
        "outputId": "9c1ec19f-0da7-4c06-c8b7-a64baca21b9a"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "iVBORw0KGgoAAAANSUhEUgAAAp8AAAHHCAYAAAD53TMPAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjcuMSwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy/bCgiHAAAACXBIWXMAAA9hAAAPYQGoP6dpAACDlUlEQVR4nOzdeVxO6f8/8NfdvhcpFVFaVCT7viVkCdmlQdYZo0GJ4WMrW5ay71tZh7EbxpKUfcmSNUsNMiayVSrScn5/+HW+bi26U3fU6/l4nMej+5zrXNf7HDe9Xee6riMRBEEAEREREZEcKJR0AERERERUdjD5JCIiIiK5YfJJRERERHLD5JOIiIiI5IbJJxERERHJDZNPIiIiIpIbJp9EREREJDdMPomIiIhIbph8EhEREZHcMPkkojJHIpHA19e3pMMoMR4eHjAzMyvzMXyPOnXqhOHDh5d0GEXK19cXEomkpMMoUo0bN8aECRNKOowfFpNPou+QRCIp0BYeHl7ssaxatQq9e/dGlSpVIJFI4OHhkWfZhIQEjBgxAgYGBtDU1ISjoyOuXbsmc5sNGzaERCLBqlWrCh3333///d0lmNl/bsOGDcv1+OTJk8Uyr169knN0hZedXGRvGhoaqFKlCrp06YKgoCCkpaWVdIii//77D76+voiMjCzpUHI4d+4cjh8/jt9//13cFx4eLt7Xq1ev5jjHw8MDWlpaRRaDh4eH1J+lqqoqrK2tMW3aNHz48KHI2vnR/f7771ixYgWeP39e0qH8kJRKOgAiymnLli1Snzdv3oyQkJAc+21tbYs9lnnz5uHdu3do2LAh4uLi8iyXlZWFzp0748aNGxg/fjwqVKiAlStXonXr1rh69SqsrKwK1N7Dhw8REREBMzMzbNu2DSNHjixU3H///TdWrFiRawL6/v17KCmVzD9/ampq2LNnD1auXAkVFRWpY3/88QfU1NSK/Zf8unXrkJWVVeT1rlq1ClpaWkhLS8OzZ89w7NgxDBkyBIsXL8ahQ4dgampa7DF8zX///Qc/Pz+YmZmhdu3acm8/PwsWLICTkxMsLS1zPe7r64u//vqr2ONQVVXF+vXrAQCJiYk4cOAAZs6ciZiYGGzbtq3Y2/8RdOvWDTo6Oli5ciVmzJhR0uH8eAQi+u6NGjVKKKm/ro8fPxaysrIEQRAETU1NYdCgQbmW27lzpwBA2LVrl7gvPj5e0NPTE9zc3Arc3rRp0wRDQ0Nhz549gkQiER49elSouEvynuUFgODq6iooKCgI+/fvlzp27tw5AYDQs2dPAYDw8uXLEopSdtOnT88z5q1btwoKCgpCo0aNZK43PT1dSEtLK4oQRREREQIAISgoqEjrTU5O/qbzX7x4ISgpKQnr16+X2h8WFiYAEGrXri0AEK5evSp1fNCgQYKmpuY3tf21+rKysoTGjRsLEolEeP78ucx1Zn8/ShtPT0+hatWq4r+PVHB87E70g0pJScG4ceNgamoKVVVVVK9eHQEBARAEQaqcRCKBp6cntm3bhurVq0NNTQ316tXD6dOnC9RO1apVCzRea/fu3ahYsSJ69Ogh7jMwMECfPn1w4MCBAj963b59O3r16gUXFxfo6upi+/btuZa7dOkSOnXqhHLlykFTUxO1atXCkiVLAHx6dLhixQoA0kMYsn0+5nP37t2QSCQ4depUjjbWrFkDiUSC27dvi/vu3buHXr16oXz58lBTU0P9+vVx8ODBAl0bAFSqVAktW7bMcV3btm2Dvb09atasmet5u3btQr169aCuro4KFSrgp59+wrNnz8TjAQEBkEgkePLkSY5zJ02aBBUVFbx9+xZA7uMts7KysHjxYtSoUQNqamqoWLEifv75Z/GcwnJ3d8ewYcNw6dIlhISEiPu/jOHx48eQSCQICAjA4sWLYWFhAVVVVdy9exdAwe97QkICvLy8YGZmBlVVVVSuXBkDBw7Eq1evEB4ejgYNGgAABg8eLH4vgoODxfO/dp+zY9fS0kJMTAw6deoEbW1tuLu7A/jUc9+zZ08YGRlBTU0NlStXRr9+/ZCYmJjvfTp8+DAyMjLQtm3bXI//9ttvKFeuXIGHkqxcuRI1atSAqqoqTExMMGrUKCQkJBTo3C9JJBI0b94cgiDgn3/+kTp25MgRtGjRApqamtDW1kbnzp1x586dAtW7detW8V6XL18e/fr1w9OnT6XKnDlzRhz2o6qqClNTU3h5eeH9+/dS5Z4/f47BgwejcuXKUFVVhbGxMbp164bHjx/LHG9B62rXrh2ePHnyXQ7h+N4x+ST6AQmCgK5du2LRokXo0KEDFi5ciOrVq2P8+PHw9vbOUf7UqVMYO3YsfvrpJ8yYMQOvX79Ghw4dpJKqb3X9+nXUrVsXCgrS/6w0bNgQqampePDgwVfruHTpEqKjo+Hm5gYVFRX06NEj18d8ISEhaNmyJe7evYsxY8YgMDAQjo6OOHToEADg559/Rrt27QB8GsKQveWmc+fO0NLSwp9//pnj2M6dO1GjRg0xIbxz5w4aN26MqKgoTJw4EYGBgdDU1ISrqyv27dv31evL1r9/f/z1119ITk4GAGRkZGDXrl3o379/ruWDg4PRp08fKCoqwt/fH8OHD8fevXvRvHlzMaHo06cPJBJJrtfx559/on379ihXrlyeMf38888YP348mjVrhiVLlmDw4MHYtm0bnJ2dkZ6eXuBry82AAQMAAMePH/9q2aCgICxbtgwjRoxAYGAgypcvX+D7npycjBYtWmDZsmVo3749lixZgl9++QX37t3Dv//+C1tbW/ER6YgRI8TvRcuWLQEU7D5ny8jIgLOzMwwNDREQEICePXvi48ePcHZ2xsWLF/Hbb79hxYoVGDFiBP7555+vJn7nz5+Hvr4+qlatmutxHR0deHl54a+//vrqOGpfX1+MGjUKJiYmCAwMRM+ePbFmzRq0b9++0H+W2YnX59+hLVu2iH9/5s2bh6lTp+Lu3bto3rx5jkTtS7Nnz8bAgQNhZWWFhQsXYuzYsQgNDUXLli2l7tWuXbuQmpqKkSNHYtmyZXB2dsayZcswcOBAqfp69uyJffv2YfDgwVi5ciVGjx6Nd+/eITY2VuZ4C1IXANSrVw/Ap7G6JKMS7nklogL48hHy/v37BQDCrFmzpMr16tVLkEgkQnR0tLgPgABAuHLlirjvyZMngpqamtC9e3eZ4sjvsbumpqYwZMiQHPsPHz4sABCOHj361fo9PT0FU1NT8THW8ePHBQDC9evXxTIZGRmCubm5ULVqVeHt27dS53/++Cu/x+4AhOnTp4uf3dzcBENDQyEjI0PcFxcXJygoKAgzZswQ9zk5OQn29vbChw8fpNps2rSpYGVl9dXrAyCMGjVKePPmjaCioiJs2bJFEIRP90gikQiPHz/O8Qj748ePgqGhoVCzZk3h/fv3Yl2HDh0SAAjTpk0T9zVp0kSoV6+eVJuXL18WAAibN28W9w0aNEioWrWq+PnMmTMCAGHbtm1S5x49ejTX/V/K77G7IAjC27dvBQBS37cvY3j06JEAQNDR0RHi4+Olzi/ofZ82bZoAQNi7d2+OGLK/G3k9dpflPg8aNEgAIEycOFGqjuvXr+cYelJQzZs3z/FnJwj/99h9165dQkJCglCuXDmha9euUrF8/pg8Pj5eUFFREdq3by9kZmaK+5cvXy4AEDZu3JhvHNn1vXz5Unj58qUQHR0tBAQECBKJRKhZs6Z4H9+9eyfo6ekJw4cPlzr/+fPngq6urtT+Lx+7P378WFBUVBRmz54tde6tW7cEJSUlqf2pqak5YvT39xckEonw5MkTQRD+7/u1YMGCPK+roPEWpK7PqaioCCNHjixQWfo/7Pkk+gH9/fffUFRUxOjRo6X2jxs3DoIg4MiRI1L7mzRpIv4vHQCqVKmCbt264dixY8jMzCySmN6/fw9VVdUc+9XU1MTj+cnIyMDOnTvRt29f8RF5mzZtYGhoKNX7ef36dTx69Ahjx46Fnp6eVB2FXc6lb9++iI+Pl1o9YPfu3cjKykLfvn0BAG/evMHJkyfRp08fvHv3Dq9evcKrV6/w+vVrODs74+HDhzkez+alXLly6NChA/744w8An4YaNG3aNNderytXriA+Ph6//vqreC+BTz22NjY2OHz4sNR1XL16FTExMeK+nTt3QlVVFd26dcsznl27dkFXVxft2rUTr+vVq1eoV68etLS0EBYWVqDrykv2bOx37959tWzPnj1hYGAgfpblvu/ZswcODg7o3r17jnq/9t2Q5T5n+3IynK6uLgDg2LFjSE1N/eq1fu7169f59kxn1z927FgcPHgQ169fz7XMiRMn8PHjR4wdO1bqKcTw4cOho6OT63V8KSUlBQYGBjAwMIClpSV8fHzQrFkzHDhwQLyPISEhSEhIgJubm9R3RlFREY0aNcr3O7N3715kZWWhT58+UucaGRnByspK6lx1dXWpuF69eoWmTZtCEATxHqirq0NFRQXh4eF5DhMpaLwFqetz5cqV+6FWpvheMPkk+gE9efIEJiYm0NbWltqfPfv9y3F/uc00t7a2RmpqKl6+fFkkMamrq+c6rjN75vbnv0Ryc/z4cbx8+RINGzZEdHQ0oqOj8ejRIzg6OuKPP/4QZ0ZnJ1Z5jY0sjA4dOkBXVxc7d+4U9+3cuRO1a9eGtbU1ACA6OhqCIGDq1KniL+bsbfr06QCA+Pj4ArfZv39/hISEIDY2Fvv378/zkXv2n2X16tVzHLOxsZH6s+7duzcUFBTE6xAEAbt27ULHjh2ho6OTZywPHz5EYmIiDA0Nc1xbcnKyTNeVm+zhBV9+X3Njbm4u9VmW+x4TE1Po74Us9xkAlJSUULly5Ryxe3t7Y/369ahQoQKcnZ2xYsWKr473zCZ8MV47N2PGjIGenl6eYz/zug4VFRVUq1Yt1zHBX1JTU0NISAhCQkIQFBQEW1tbxMfHS/0dfvjwIYBP/0H88s/l+PHj+X5nHj58CEEQYGVllePcqKgoqXNjY2Ph4eGB8uXLQ0tLCwYGBmjVqhUAiPdVVVUV8+bNw5EjR1CxYkW0bNkS8+fPl1oGqaDxFqSuzwmCUOrWMJUHLrVEREXC2Ng416WYsveZmJjke35272afPn1yPX7q1Ck4Ojp+Y5S5U1VVFccPrly5Ei9evMC5c+cwZ84csUx28uvj4wNnZ+dc68lriZzcdO3aFaqqqhg0aBDS0tLyvG5ZmJiYoEWLFvjzzz/xv//9DxcvXkRsbCzmzZuX73lZWVk5epg/93lPZGFkjy0uyP358j8pRX3fi4qqqmqO8c0AEBgYCA8PDxw4cADHjx/H6NGj4e/vj4sXL+ZIVj+nr69foJ627N5PX1/fPHs/v5WioqLUxCdnZ2fY2Njg559/Fid5Zf+5bNmyBUZGRjnqyG8ps6ysLEgkEhw5cgSKioo5jmf3lGdmZqJdu3Z48+YNfv/9d9jY2EBTUxPPnj2Dh4eH1FJdY8eORZcuXbB//34cO3YMU6dOhb+/P06ePIk6derIFO/X6vpcQkICKlSokOe1Uu6YfBL9gKpWrYoTJ07g3bt3Ur1J9+7dE49/Lvt//Z978OABNDQ0vjmxyFa7dm2cOXMGWVlZUr+UL126BA0NDbEHMTcpKSk4cOAA+vbti169euU4Pnr0aGzbtg2Ojo6wsLAA8CmhyWtmMCD7I/i+ffti06ZNCA0NRVRUFARBEB+5A0C1atUAAMrKyvm2W1Dq6upwdXXF1q1b0bFjxzx/gWX/Wd6/fx9t2rSROnb//v0cf9Z9+/bFr7/+ivv372Pnzp3Q0NBAly5d8o3FwsICJ06cQLNmzb7aQ10Y2ZO98koe8yPLfbewsPjqJLq8vhey3uf82Nvbw97eHlOmTMH58+fRrFkzrF69GrNmzcrzHBsbG+zZs6dA9Y8dOxaLFy+Gn59fjqEnn19H9r0DgI8fP+LRo0eF+u4aGxvDy8sLfn5+uHjxIho3biz+PTQ0NJS5TgsLCwiCAHNz83z/Xbh16xYePHiATZs2SU0w+nzVhC/rHTduHMaNG4eHDx+idu3aCAwMxNatW2WON7+6sj179gwfP36Uy3rLpQ0fuxP9gDp16oTMzEwsX75cav+iRYsgkUjQsWNHqf0XLlyQmiH79OlTHDhwAO3bt8+156EwevXqhRcvXmDv3r3ivlevXmHXrl3o0qVLruNBs+3btw8pKSkYNWoUevXqlWNzcXHBnj17kJaWhrp168Lc3ByLFy/OMYP488eWmpqaAFDg5WXatm2L8uXLY+fOndi5cycaNmwo9QjY0NAQrVu3xpo1a3Lt4S3M8AUfHx9Mnz4dU6dOzbNM/fr1YWhoiNWrV0sNazhy5AiioqLQuXNnqfI9e/aEoqIi/vjjD+zatQsuLi7ivchLnz59kJmZiZkzZ+Y4lpGRUegleoBP41nXr1+PJk2awMnJSebzZbnvPXv2xI0bN3JdeSD7u5HX90LW+5ybpKQkZGRkSO2zt7eHgoLCV5caa9KkCd6+fZtjKaPcZPd+HjhwIMcyP23btoWKigqWLl0q9fdhw4YNSExMlLqO2NhY8T+sX/Pbb79BQ0MDc+fOBfDpPxI6OjqYM2dOrjPo8/v70KNHDygqKsLPzy/HUANBEPD69WsAEP9t+ryMIAjikmrZUlNTc7yYwcLCAtra2uJ9L2i8BakrW/Ybp5o2bZrntVLu2PNJ9APq0qULHB0dMXnyZDx+/BgODg44fvw4Dhw4gLFjx4r/y89Ws2ZNODs7Y/To0VBVVcXKlSsBAH5+fl9t66+//sKNGzcAAOnp6bh586bYg9O1a1fUqlULwKfks3Hjxhg8eDDu3r0rvuEoMzPzq+1s27YN+vr6ef4j3rVrV6xbtw6HDx9Gjx49sGrVKnTp0gW1a9fG4MGDYWxsjHv37uHOnTs4duwYgP9bBmX06NFwdnaGoqIi+vXrl2cMysrK6NGjB3bs2IGUlBQEBATkKLNixQo0b94c9vb2GD58OKpVq4YXL17gwoUL+Pfff8X7VFAODg5wcHDIt4yysjLmzZuHwYMHo1WrVnBzc8OLFy+wZMkSmJmZwcvLS6q8oaEhHB0dsXDhQrx7906q9zYvrVq1ws8//wx/f39ERkaiffv2UFZWxsOHD7Fr1y4sWbIk1x7pL+3evRtaWlr4+PGj+Iajc+fOwcHBAbt27frq+Xkp6H0fP348du/ejd69e2PIkCGoV68e3rx5g4MHD2L16tVwcHCAhYUF9PT0sHr1amhra0NTUxONGjWCubm5TPc5NydPnoSnpyd69+4Na2trZGRkYMuWLVBUVETPnj3zPbdz585QUlLCiRMnMGLEiK+2NWbMGCxatAg3btyQ+s+FgYEBJk2aBD8/P3To0AFdu3bF/fv3sXLlSjRo0AA//fSTWHbgwIE4depUgcaa6uvri0sPRUVFwdbWFqtWrcKAAQNQt25d9OvXDwYGBoiNjcXhw4fRrFmzHP85zmZhYYFZs2Zh0qRJePz4MVxdXaGtrY1Hjx5h3759GDFiBHx8fGBjYwMLCwv4+Pjg2bNn0NHRwZ49e3IMT3jw4AGcnJzQp08f2NnZQUlJCfv27cOLFy/Ev/M6OjoFircgdWULCQlBlSpVcjyKpwKQ9/R6IpJdbssGvXv3TvDy8hJMTEwEZWVlwcrKSliwYEGOt23g/y/vs3XrVsHKykpQVVUV6tSpI4SFhRWo7exlZXLbvlyu5s2bN8LQoUMFfX19QUNDQ2jVqpUQERGRb/3Zb3YZMGBAnmVSU1MFDQ0NqaV6zp49K7Rr107Q1tYWNDU1hVq1agnLli0Tj2dkZAi//fabYGBgIEgkEqn7hy+WWsoWEhIiABAkEonw9OnTXGOJiYkRBg4cKBgZGQnKyspCpUqVBBcXF2H37t35Xmd2u6NGjcq3TF7LFu3cuVOoU6eOoKqqKpQvX15wd3cX/v3331zrWLdunQBA0NbWllo2KNuXyxxlW7t2rVCvXj1BXV1d0NbWFuzt7YUJEyYI//33X4Fizt7U1NSEypUrCy4uLsLGjRullkjKK4bspZbyWuKmoPf99evXgqenp1CpUiVBRUVFqFy5sjBo0CDh1atXYpkDBw4IdnZ2gpKSUo7vcUHuc15vFfrnn3+EIUOGCBYWFoKamppQvnx5wdHRUThx4kS+9y9b165dBScnJ6l9ny+19KXs+55bLMuXLxdsbGwEZWVloWLFisLIkSNzLE3WqlWrHP+u5PfGpJiYGEFRUVFqubWwsDDB2dlZ0NXVFdTU1AQLCwvBw8NDamm3vN5wtGfPHqF58+aCpqamoKmpKdjY2AijRo0S7t+/L5a5e/eu0LZtW0FLS0uoUKGCMHz4cOHGjRtSf26vXr0SRo0aJdjY2AiampqCrq6u0KhRI+HPP//M0ebX4i1oXZmZmYKxsbEwZcqUXO8V5U8iCAX4Lw8R/bAkEglGjRqVZy8EEX0fzpw5g9atW+PevXu5rlBB34/sFSpiYmJgbGxc0uH8cDjmk4iI6DvQokULtG/fHvPnzy/pUOgr5s2bB09PTyaehcQxn0RERN+JL18QQd+nCxculHQIPzT2fBIRERGR3LDnk6iU47BuIiL6nrDnk4iIiIjkhsknEREREckNH7vTdycrKwv//fcftLW1ZX5FIhEREZUMQRDw7t07mJiYSL1m+UtMPum7899//8HU1LSkwyAiIqJCePr0KSpXrpzncSaf9N3R1tYG8OnLq6OjU8LREBERUUEkJSXB1NRU/D2eFyaf9N3JftSuo6PD5JOIiOgH87Uhc5xwRERERERyw+STiIiIiOSGyScRERERyQ2TTyIiIiKSGyafRERERCQ3TD6JiIiISG6YfBIRERGR3DD5JCIiIiK5YfJJRERERHLD5JOIiIiI5IbJJxERERHJDZNPIiIiIpIbJp9EREREJDdMPomIiIhIbpRKOgCivHTuDCjxG0plQFhYSUdARCQ/7PkkIiIiIrlh8klEREREcsPkk4iIiIjkhsknEREREckNk08iIiIikhsmn0REREQkN0w+iYiIiEhumHwWEw8PD7i6upZ0GDIrirjDw8MhkUiQkJAAAAgODoaent43x0ZEREQ/vlKffHp4eEAikeTYoqOjSzq0HLJju3jxotT+tLQ06OvrQyKRIDw8vGSCIyIiIioCpT75BIAOHTogLi5OajM3N89R7uPHjyUQnTRTU1MEBQVJ7du3bx+0tLS+ue7v4fqIiIiobCsTyaeqqiqMjIykNkVFRbRu3Rqenp4YO3YsKlSoAGdnZwDAwoULYW9vD01NTZiamuLXX39FcnKyWF/2Y+Rjx47B1tYWWlpaYoKbl4iICBgYGGDevHn5xjpo0CDs2LED79+/F/dt3LgRgwYNylH2999/h7W1NTQ0NFCtWjVMnToV6enp4nFfX1/Url0b69evh7m5OdTU1AAAu3fvhr29PdTV1aGvr4+2bdsiJSVFqu6AgAAYGxtDX18fo0aNkqp3y5YtqF+/PrS1tWFkZIT+/fsjPj4+3+siIiIiAspI8pmfTZs2QUVFBefOncPq1asBAAoKCli6dCnu3LmDTZs24eTJk5gwYYLUeampqQgICMCWLVtw+vRpxMbGwsfHJ9c2Tp48iXbt2mH27Nn4/fff842nXr16MDMzw549ewAAsbGxOH36NAYMGJCjrLa2NoKDg3H37l0sWbIE69atw6JFi6TKREdHY8+ePdi7dy8iIyMRFxcHNzc3DBkyBFFRUQgPD0ePHj0gCIJ4TlhYGGJiYhAWFoZNmzYhODgYwcHB4vH09HTMnDkTN27cwP79+/H48WN4eHjke11EREREAKBU0gHIw6FDh6QeW3fs2BG7du0CAFhZWWH+/PlS5ceOHSv+bGZmhlmzZuGXX37BypUrxf3p6elYvXo1LCwsAACenp6YMWNGjrb37duHgQMHYv369ejbt2+B4h0yZAg2btyIn376CcHBwejUqRMMDAxylJsyZYpUnD4+PtixY4dUovzx40ds3rxZPP/atWvIyMhAjx49ULVqVQCAvb29VL3lypXD8uXLoaioCBsbG3Tu3BmhoaEYPny4GF+2atWqYenSpWjQoAGSk5MLNTwgLS0NaWlp4uekpCSZ6yAiIqIfQ5lIPh0dHbFq1Srxs6ampvhzvXr1cpQ/ceIE/P39ce/ePSQlJSEjIwMfPnxAamoqNDQ0AAAaGhpi4gkAxsbGOR49X7p0CYcOHcLu3btlmkH+008/YeLEifjnn38QHByMpUuX5lpu586dWLp0KWJiYpCcnIyMjAzo6OhIlalatapU4urg4AAnJyfY29vD2dkZ7du3R69evVCuXDmxTI0aNaCoqCh1bbdu3RI/X716Fb6+vrhx4wbevn2LrKwsAJ96ae3s7Ap8ndn8/f3h5+cn83lERET04ykTj901NTVhaWkpbsbGxlLHPvf48WO4uLigVq1a2LNnD65evYoVK1YAkJ6wo6ysLHWeRCKRenQNABYWFrCxscHGjRulxkx+jb6+PlxcXDB06FB8+PABHTt2zFHmwoULcHd3R6dOnXDo0CFcv34dkydPzjGp6MvrU1RUREhICI4cOQI7OzssW7YM1atXx6NHj/K9tuwEMyUlBc7OztDR0cG2bdsQERGBffv2ASj8hKZJkyYhMTFR3J4+fVqoeoiIiOj7VyaST1lcvXoVWVlZCAwMROPGjWFtbY3//vuvUHVVqFABJ0+eRHR0NPr06SNTAjpkyBCEh4dj4MCBUr2Q2c6fP4+qVati8uTJqF+/PqysrPDkyZMC1S2RSNCsWTP4+fnh+vXrUFFRERPIr7l37x5ev36NuXPnokWLFrCxsfnmyUaqqqrQ0dGR2oiIiKh0KhOP3WVhaWmJ9PR0LFu2DF26dJGaiFQYhoaGOHnyJBwdHeHm5oYdO3ZASenrt71Dhw54+fJlnomYlZUVYmNjsWPHDjRo0ACHDx8uUAJ56dIlhIaGon379jA0NMSlS5fw8uVL2NraFuh6qlSpAhUVFSxbtgy//PILbt++jZkzZxboXCIiIiL2fH7BwcEBCxcuxLx581CzZk1s27YN/v7+31SnkZERTp48iVu3bsHd3R2ZmZlfPUcikaBChQpQUVHJ9XjXrl3h5eUFT09P1K5dG+fPn8fUqVO/Wq+Ojg5Onz6NTp06wdraGlOmTEFgYGCuj/ZzY2BggODgYOzatQt2dnaYO3cuAgICCnQuERERkUT4cqAiUQlLSkqCrq4umjdPhJISH8FT6RcWVtIREBF9u+zf34mJifkOoWPPJxERERHJDZNPIiIiIpIbJp9EREREJDdMPomIiIhIbph8EhEREZHcMPkkIiIiIrlh8klEREREcsM3HNF36/BhgG/aJCIiKl3Y80lEREREcsPkk4iIiIjkhsknEREREckNk08iIiIikhsmn0REREQkN0w+iYiIiEhuuNQSfbc6dwaU+A2lMiAsrKQjICKSH/Z8EhEREZHcMPkkIiIiIrlh8klEREREcsPkk4iIiIjkhsknEREREckNk08iIiIikhsmn0REREQkN0w+iYiIiEhumHx+hYeHB1xdXUs6jG/i6+uL2rVr51tm//79sLS0hKKiIsaOHVuk7QcHB0NPT69I6yQiIqIf0w+ffEokknw3X1/fkg4xTxKJBPv378+xvyQS3p9//hm9evXC06dPMXPmTLm2TURERGXHD//ywri4OPHnnTt3Ytq0abh//764T0tLqyTCEgmCgMzMTCh9x++JTE5ORnx8PJydnWFiYlLoej5+/AgVFZUijIyIiIhKmx++59PIyEjcdHV1IZFIxM8pKSlwd3dHxYoVoaWlhQYNGuDEiRPiuTNmzEDNmjVz1Fm7dm1MnTo11/bS0tIwevRoGBoaQk1NDc2bN0dERIR4PDw8HBKJBEeOHEG9evWgqqqKs2fPftM1Hj16FM2bN4eenh709fXh4uKCmJgYqTL//vsv3NzcUL58eWhqaqJ+/fq4dOlSrvXFxMSgWrVq8PT0RFhYGLS1tQEAbdq0gUQiQXh4OABgz549qFGjBlRVVWFmZobAwECpeszMzDBz5kwMHDgQOjo6GDFiBIBPj9mrVKkCDQ0NdO/eHa9fv/6m6yciIqLS44dPPvOTnJyMTp06ITQ0FNevX0eHDh3QpUsXxMbGAgCGDBmCqKgoqeTx+vXruHnzJgYPHpxrnRMmTMCePXuwadMmXLt2DZaWlnB2dsabN2+kyk2cOBFz585FVFQUatWq9U3XkZKSAm9vb1y5cgWhoaFQUFBA9+7dkZWVJV5nq1at8OzZMxw8eBA3btzAhAkTxOOfu3nzJpo3b47+/ftj+fLlaNasmdhTvGfPHsTFxaFp06a4evUq+vTpg379+uHWrVvw9fXF1KlTERwcLFVfQEAAHBwccP36dUydOhWXLl3C0KFD4enpicjISDg6OmLWrFn5Xl9aWhqSkpKkNiIiIiqdvt9nwUXAwcEBDg4O4ueZM2di3759OHjwIDw9PVG5cmU4OzsjKCgIDRo0AAAEBQWhVatWqFatWo76UlJSsGrVKgQHB6Njx44AgHXr1iEkJAQbNmzA+PHjxbIzZsxAu3btvhqjm5sbFBUVpfalpaWhc+fO4ueePXtKHd+4cSMMDAxw9+5d1KxZE9u3b8fLly8RERGB8uXLAwAsLS1ztHX+/Hm4uLhg8uTJGDduHABARUUFhoaGAIDy5cvDyMgIALBw4UI4OTmJPcDW1ta4e/cuFixYAA8PD7HONm3aiHUBwNSpU9GhQwdMmDBBPO/8+fM4evRonvfA398ffn5++d8oIiIiKhVKfc+nj48PbG1toaenBy0tLURFRYk9nwAwfPhw/PHHH/jw4QM+fvyI7du3Y8iQIbnWFxMTg/T0dDRr1kzcp6ysjIYNGyIqKkqqbP369QsU46JFixAZGSm1de3aVarMw4cP4ebmhmrVqkFHRwdmZmYAIF5HZGQk6tSpIyaeuYmNjUW7du0wbdo0qWQxL1FRUVLXCQDNmjXDw4cPkZmZmed1RkVFoVGjRlL7mjRpkm9bkyZNQmJiorg9ffr0q/ERERHRj6lU93z6+PggJCQEAQEBsLS0hLq6Onr16oWPHz+KZbp06QJVVVXs27cPKioqSE9PR69evb65bU1NzQKVMzIyytFLqa2tjYSEBKkYq1atinXr1sHExARZWVmoWbOmeB3q6upfbcfAwAAmJib4448/MGTIEOjo6BT8YvJR0OvMj6qqKlRVVYsgGiIiIvreleqez3PnzsHDwwPdu3eHvb09jIyM8PjxY6kySkpKGDRoEIKCghAUFIR+/frlmcxZWFhARUUF586dE/elp6cjIiICdnZ2xXINr1+/xv379zFlyhQ4OTnB1tYWb9++lSpTq1YtREZG5hh3+jl1dXUcOnQIampqcHZ2xrt37/Jt19bWVuo6gU/309raOscwgS/P+3Ki08WLF/Nti4iIiMqOUp18WllZYe/evYiMjMSNGzfQv3//XCfhDBs2DCdPnsTRo0fzfOQOfOrlGzlyJMaPH4+jR4/i7t27GD58OFJTUzF06NBiuYZy5cpBX18fa9euRXR0NE6ePAlvb2+pMm5ubjAyMoKrqyvOnTuHf/75B3v27MGFCxdyxH/48GEoKSmhY8eOSE5OzrPdcePGITQ0FDNnzsSDBw+wadMmLF++HD4+PvnGO3r0aBw9ehQBAQF4+PAhli9fnu94TyIiIipbSnXyuXDhQpQrVw5NmzZFly5d4OzsjLp16+YoZ2VlhaZNm8LGxibHeMUvzZ07Fz179sSAAQNQt25dREdH49ixYyhXrlyxXIOCggJ27NiBq1evombNmvDy8sKCBQukyqioqOD48eMwNDREp06dYG9vj7lz5+baQ6mlpYUjR45AEAR07twZKSkpubZbt25d/Pnnn9ixYwdq1qyJadOmYcaMGVKTjXLTuHFjrFu3DkuWLIGDgwOOHz+OKVOmFPr6iYiIqHSRCIIglHQQJU0QBFhZWeHXX3/N0atI8peUlARdXV00b54IJaWiGZtK9D0LCyvpCIiIvl327+/ExMR855aU6glHBfHy5Uvs2LEDz58/z3NtTyIiIiIqGmU++TQ0NESFChWwdu3aYnt0TkRERESflPnkk6MOiIiIiOSnVE84IiIiIqLvC5NPIiIiIpIbJp9EREREJDdMPomIiIhIbsr8hCP6fh0+DBTRK+iJiIjoO8GeTyIiIiKSGyafRERERCQ3TD6JiIiISG6YfBIRERGR3DD5JCIiIiK54Wx3+m517gwo8RtKZUBYWElHQEQkP+z5JCIiIiK5YfJJRERERHLD5JOIiIiI5IbJJxERERHJDZNPIiIiIpIbJp9EREREJDdMPomIiIhIbph8EhEREZHcMPkkIiIiIrkpc8mnh4cHJBIJJBIJlJWVYW5ujgkTJuDDhw/F3rZEIsH+/fuLvR0iIiKi71WZfHlhhw4dEBQUhPT0dFy9ehWDBg2CRCLBvHnzSjq0YpOZmQmJRAIFhTL3/w0iIiL6jpTJTERVVRVGRkYwNTWFq6sr2rZti5CQEPH469ev4ebmhkqVKkFDQwP29vb4448/xOObN2+Gvr4+0tLSpOp1dXXFgAEDChXT19o8dOgQ9PT0kJmZCQCIjIyERCLBxIkTxTLDhg3DTz/9BAAIDg6Gnp4eDh48CDs7O6iqqiI2NhZpaWnw8fFBpUqVoKmpiUaNGiE8PFysI/u8Y8eOwdbWFlpaWujQoQPi4uKk4t24cSNq1KgBVVVVGBsbw9PTUzyWkJCAYcOGwcDAADo6OmjTpg1u3LhRqPtCREREpUuZTD4/d/v2bZw/fx4qKirivg8fPqBevXo4fPgwbt++jREjRmDAgAG4fPkyAKB3797IzMzEwYMHxXPi4+Nx+PBhDBkypFBxfK3NFi1a4N27d7h+/ToA4NSpU6hQoYJU4njq1Cm0bt1a/Jyamop58+Zh/fr1uHPnDgwNDeHp6YkLFy5gx44duHnzJnr37o0OHTrg4cOHUucFBARgy5YtOH36NGJjY+Hj4yMeX7VqFUaNGoURI0bg1q1bOHjwICwtLcXjvXv3Rnx8PI4cOYKrV6+ibt26cHJywps3b3K99rS0NCQlJUltREREVDpJBEEQSjoIefLw8MDWrVuhpqaGjIwMpKWlQUFBAX/++Sd69uyZ53kuLi6wsbFBQEAAAODXX3/F48eP8ffffwMAFi5ciBUrViA6OhoSiSTXOiQSCfbt2wdXV9cCxfplm/Xq1YObmxt8fHzQvXt3NGjQAH5+fnj9+jUSExNRuXJlPHjwAFZWVggODsbgwYMRGRkJBwcHAEBsbCyqVauG2NhYmJiYiO20bdsWDRs2xJw5c8TzoqOjYWFhAQBYuXIlZsyYgefPnwMAKlWqhMGDB2PWrFk5Yj579iw6d+6M+Ph4qKqqivstLS0xYcIEjBgxIsc5vr6+8PPzy7G/efNEKCnpFOheEf3IwsJKOgIiom+XlJQEXV1dJCYmQkcn79/fZXLMp6OjI1atWoWUlBQsWrQISkpKUolnZmYm5syZgz///BPPnj3Dx48fkZaWBg0NDbHM8OHD0aBBAzx79gyVKlVCcHCwOJmpMArSZqtWrRAeHo5x48bhzJkz8Pf3x59//omzZ8/izZs3MDExgZWVlVheRUUFtWrVEj/funULmZmZsLa2lmo7LS0N+vr64mcNDQ0x8QQAY2NjxMfHA/jUw/vff//Byckp1+u4ceMGkpOTpeoDgPfv3yMmJibXcyZNmgRvb2/xc1JSEkxNTfO8V0RERPTjKpPJp6ampviYeOPGjXBwcMCGDRswdOhQAMCCBQuwZMkSLF68GPb29tDU1MTYsWPx8eNHsY46derAwcEBmzdvRvv27XHnzh0cPny40DEVpM3WrVtj48aNuHHjBpSVlWFjY4PWrVsjPDwcb9++RatWraTqVFdXl0qGk5OToaioiKtXr0JRUVGqrJaWlvizsrKy1DGJRILsDnJ1dfV8ryM5ORnGxsZSwwGy6enp5XqOqqqqVC8pERERlV5FknwmJCTkmVh87xQUFPC///0P3t7e6N+/P9TV1XHu3Dl069ZNnLyTlZWFBw8ewM7OTurcYcOGYfHixXj27Bnatm37Tb11BWkze9znokWLxESzdevWmDt3Lt6+fYtx48bl20adOnWQmZmJ+Ph4tGjRolBxamtrw8zMDKGhoXB0dMxxvG7dunj+/DmUlJRgZmZWqDaIiIio9JJ5wtG8efOwc+dO8XOfPn2gr6+PSpUq/bAzmnv37g1FRUWsWLECAGBlZYWQkBCcP38eUVFR+Pnnn/HixYsc5/Xv3x///vsv1q1bV+CJRo8ePUJkZKTUlpKSUqA2y5Urh1q1amHbtm3ixKKWLVvi2rVrePDgQY6ezy9ZW1vD3d0dAwcOxN69e/Ho0SNcvnwZ/v7+MvXa+vr6IjAwEEuXLsXDhw9x7do1LFu2DMCn8aNNmjSBq6srjh8/jsePH+P8+fOYPHkyrly5UuA2iIiIqHSSOflcvXq12MMXEhKCkJAQHDlyBB07dsT48eOLPEB5UFJSgqenJ+bPn4+UlBRMmTIFdevWhbOzM1q3bg0jI6NcJwnp6uqiZ8+e0NLSKvAkIm9vb9SpU0dqu379eoHbbNWqFTIzM8Xks3z58rCzs4ORkRGqV6/+1faDgoIwcOBAjBs3DtWrV4erqysiIiJQpUqVAsUPAIMGDcLixYuxcuVK1KhRAy4uLuJseYlEgr///hstW7bE4MGDYW1tjX79+uHJkyeoWLFigdsgIiKi0knm2e7q6up48OABTE1NMWbMGHz48AFr1qzBgwcP0KhRI7x9+7a4Yv0uOTk5oUaNGli6dGlJh1JqZM+W42x3Kis4252ISoOCznaXueezXLlyePr0KQDg6NGjaNu2LQBAEARxAfSy4O3bt9i3bx/Cw8MxatSokg6HiIiI6Icg84SjHj16oH///rCyssLr16/RsWNHAMD169elFhov7erUqYO3b99i3rx5BXrcTURERESFSD4XLVoEMzMzPH36FPPnzxeX6ImLi8Ovv/5a5AF+rx4/flzSIRARERH9cMrcG47o+8cxn1TWcMwnEZUGxTbmEwC2bNmC5s2bw8TEBE+ePAEALF68GAcOHChctERERERUJsicfK5atQre3t7o2LEjEhISxElGenp6WLx4cVHHR0RERESliMzJ57Jly7Bu3TpMnjxZ6hWN9evXx61bt4o0OCIiIiIqXWSecPTo0SPUqVMnx35VVVWkpKQUSVBEAHD4MJDPkBEiIiL6Acnc82lubo7IyMgc+48ePQpbW9uiiImIiIiISimZez69vb0xatQofPjwAYIg4PLly/jjjz/g7++P9evXF0eMRERERFRKyJx8Dhs2DOrq6pgyZQpSU1PRv39/mJiYYMmSJejXr19xxEhEREREpcQ3rfOZmpqK5ORkGBoaFmVMVMYVdJ0wIiIi+n4U2zqf79+/R2pqKgBAQ0MD79+/x+LFi3H8+PHCR0tEREREZYLMyWe3bt2wefNmAEBCQgIaNmyIwMBAdOvWDatWrSryAImIiIio9JB5zOe1a9ewaNEiAMDu3bthZGSE69evY8+ePZg2bRpGjhxZ5EFS2dS5M6Ak8zeU6MfD12sSUVkic89namoqtLW1AQDHjx9Hjx49oKCggMaNG4uv2iQiIiIiyo3MyaelpSX279+Pp0+f4tixY2jfvj0AID4+npNDiIiIiChfMief06ZNg4+PD8zMzNCoUSM0adIEwKde0NzefERERERElE3mEXW9evVC8+bNERcXBwcHB3G/k5MTunfvXqTBEREREVHpUqjpHEZGRjAyMpLa17BhwyIJiIiIiIhKr0Iln1euXMGff/6J2NhYfPz4UerY3r17iyQwIiIiIip9ZB7zuWPHDjRt2hRRUVHYt28f0tPTcefOHZw8eRK6urrFESMRERERlRIyJ59z5szBokWL8Ndff0FFRQVLlizBvXv30KdPH1Sp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bo6goKBCTW7KtnHjRnTv3j1H4pl9HQMGDMCrV68KVNe4ceMQFxeHQYMGQUFBAUOGDEH37t2lhiDMnDkTBgYG8Pf3xz///AM9PT3UrVsX//vf//KsV1FREa9fv8bAgQPx4sULVKhQAT169ICfn5/sF0xERESljkQo7FpDRMUkKSkJurq6aN48EUpKfARPpd8XK7AREf2Qsn9/JyYm5juETqYxn0RERERE34LJJxERERHJDZNPIiIiIpIbJp9EREREJDdMPomIiIhIbph8EhEREZHcMPkkIiIiIrkpE4vM04/p8GGAb9okIiIqXdjzSURERERyw+STiIiIiOSGyScRERERyQ2TTyIiIiKSGyafRERERCQ3TD6JiIiISG641BJ9tzp3BpT4DSUiKnXCwko6AipJ7PkkIiIiIrlh8klEREREcsPkk4iIiIjkhsknEREREckNk08iIiIikhsmn0REREQkN0w+iYiIiEhumHwSERERkdyUmeTz8ePHkEgkiIyMzLNMeHg4JBIJEhIS5BZXSSgr10lERETfnxJNPj08PCCRSCCRSKCsrIyKFSuiXbt22LhxI7Kysoq0LVNTU8TFxaFmzZrfXNf169fRu3dvVKxYEWpqarCyssLw4cPx4MGDIoiUiIiIqPQq8Z7PDh06IC4uDo8fP8aRI0fg6OiIMWPGwMXFBRkZGUXWjqKiIoyMjKD0je9rPHToEBo3boy0tDRs27YNUVFR2Lp1K3R1dTF16tRczxEEoUiv5Xv18ePHkg6BiIiIvnMlnnyqqqrCyMgIlSpVQt26dfG///0PBw4cwJEjRxAcHCyWW7hwIezt7aGpqQlTU1P8+uuvSE5OBgAkJSVBXV0dR44ckap737590NbWRmpqaq6P3f/++29YW1tDXV0djo6OePz4cb6xpqamYvDgwejUqRMOHjyItm3bwtzcHI0aNUJAQADWrFkD4P8eax85cgT16tWDqqoqzp49i7S0NIwePRqGhoZQU1ND8+bNERERIdaffV5oaCjq168PDQ0NNG3aFPfv35eK48CBA6hbty7U1NRQrVo1+Pn5SSW3EokE69evR/fu3aGhoQErKyscPHgwx/WcO3cOtWrVgpqaGho3bozbt29LHT979ixatGgBdXV1mJqaYvTo0UhJSRGPm5mZYebMmRg4cCB0dHQwYsQIAMC6detgamoKDQ0N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XTtoamriyJEj2LRpE1auXFnSYREREdF3gMknFbnLly9j/vz5ePfuHapVq4alS5di2LBhJR0WERERfQeYfFKRy20lAiIiIiLgO5hwRERERERlB5NPIiIiIpIbJp9EREREJDdMPomIiIhIbjjhiL5bhw8D+SwTRkRERD8g9nwSERERkdww+SQiIiIiuWHySURERERyw+STiIiIiOSGyScRERERyQ1nu9N3q3NnQInfUCIioiITFlbSEbDnk4iIiIjkiMknEREREckNk08iIiIikhsmn0REREQkN0w+iYiIiEhumHwSERERkdww+SQiIiIiuWHySURERERyU+aSz/DwcEgkEiQkJAAAgoODoaenJx739fVF7dq1xc8eHh5wdXWVa4yF9WXshfH48WNIJBJERkYCyHm/vlaeiIiIKD8/bPK5evVqaGtrIyMjQ9yXnJwMZWVltG7dWqpsdgIVExODpk2bIi4uDrq6ugVqZ8mSJQgODi7CyAsmO6n7cvvpp5/yPMfHxwehoaFyjBIwNTVFXFwcatasKdd2iYiI6Mf0w7680NHREcnJybhy5QoaN24MADhz5gyMjIxw6dIlfPjwAWpqagCAsLAwVKlSBRYWFgAAIyOjArdT0CS1uJw4cQI1atQQP6urq+coIwgCMjMzoaWlBS0tLXmGB0VFRZnuJxEREZVtP2zPZ/Xq1WFsbIzw8HBxX3h4OLp16wZzc3NcvHhRar+jo6P4c36Pkb/05WP3o0ePonnz5tDT04O+vj5cXFwQExMjHs/usfzzzz/RokULqKuro0GDBnjw4AEiIiJQv359aGlpoWPHjnj58uVX29fX14eRkZG46erqitdw5MgR1KtXD6qqqjh79myuj93Xr18PW1tbqKmpwcbGBitXrpQ6fvnyZdSpUwdqamqoX78+rl+/nm88qamp6NixI5o1a4aEhIQ8H9OHhoaifv360NDQQNOmTXH//v2vXisRERGVfj9s8gl86v0MCwsTP4eFhaF169Zo1aqVuP/9+/e4dOmSmHx+q5SUFHh7e+PKlSsIDQ2FgoICunfvjqysLKly06dPx5QpU3Dt2jUoKSmhf//+mDBhApYsWYIzZ84gOjoa06ZN+6ZYJk6ciLlz5yIqKgq1atXKcXzbtm2YNm0aZs+ejaioKMyZMwdTp07Fpk2bAHwapuDi4gI7OztcvXoVvr6+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\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [],
      "metadata": {
        "id": "smgM7clQbYpy"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "movie_information.groupby('rating')['director'].sum()\n",
        "print(movie_information.groupby('rating')['director'].sum())"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "24aIU9jY4fOR",
        "outputId": "a86552cd-9282-4eff-86e8-3496ae478827"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "rating\n",
            "G        Roy RowlandJohn LasseterMichael RubboLeo McCar...\n",
            "NC17                                           John Waters\n",
            "NR       Rodney BennettWilliam WellmanEdward DmytrykTer...\n",
            "PG       Jay RussellRick RosenthalMartyn BurkeSteve Boy...\n",
            "PG-13    Jake KasdanFrank MarshallWilliam FriedkinCarl ...\n",
            "R        William FriedkinDavid CronenbergAllison Anders...\n",
            "Name: director, dtype: object\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#Check on the missing data. \n",
        "movie_information.isna().sum()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "5sVOViZTeAE9",
        "outputId": "9edc7832-9097-4c25-eef2-57da85b690ad"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "synopsis          62\n",
              "rating             3\n",
              "genre              8\n",
              "director         199\n",
              "writer           449\n",
              "theater_date     359\n",
              "dvd_date         359\n",
              "currency        1220\n",
              "box_office      1220\n",
              "runtime           30\n",
              "studio          1066\n",
              "dtype: int64"
            ]
          },
          "metadata": {},
          "execution_count": 11
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Identify the relevant columns for your analysis and create a new dataframe."
      ],
      "metadata": {
        "id": "gaKSS7iNgvdx"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "relevant_columns=['rating','genre','runtime','director','theater_date']"
      ],
      "metadata": {
        "id": "xGErkNXHi1NS"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "#create a new dataframe and check for missing data.\n",
        "summary_columns = movie_information[relevant_columns]\n",
        "summary_columns.isna().describe"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "_fA7a6WavwxJ",
        "outputId": "790112f4-d53f-48f8-c988-0a20b7e70861"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "<bound method NDFrame.describe of       rating  genre  runtime  director  theater_date\n",
              "id                                                  \n",
              "1      False  False    False     False         False\n",
              "3      False  False    False     False         False\n",
              "5      False  False    False     False         False\n",
              "6      False  False    False     False         False\n",
              "7      False  False    False     False          True\n",
              "...      ...    ...      ...       ...           ...\n",
              "1996   False  False    False      True         False\n",
              "1997   False  False    False     False         False\n",
              "1998   False  False    False     False         False\n",
              "1999   False  False    False     False         False\n",
              "2000   False  False    False      True         False\n",
              "\n",
              "[1560 rows x 5 columns]>"
            ]
          },
          "metadata": {},
          "execution_count": 13
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#Drop data from rows with NAN values from the selected columns in the new dataframe\n",
        "clean_columns_mov_info = summary_columns.dropna(axis =0,subset =['director','theater_date','runtime'])"
      ],
      "metadata": {
        "id": "4OJNtNZ0HC4y"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "#Check the significance difference after dropping.\n",
        "clean_columns_mov_info.shape"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "YagtCgKTIMDj",
        "outputId": "fb678d8d-f4c0-41e9-f6c0-7b11988f61f8"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "(1076, 5)"
            ]
          },
          "metadata": {},
          "execution_count": 15
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#summary_columns\n",
        "#import datetime\n",
        "#Split the theater date columns into %dd%mm%yy and add to the new dataframe- convert the running time to hours\n",
        "clean_columns_mov_info['month'] = clean_columns_mov_info['theater_date'].dt.month\n",
        "clean_columns_mov_info['year'] = clean_columns_mov_info['theater_date'].dt.year\n",
        "clean_columns_mov_info['date'] = clean_columns_mov_info['theater_date'].dt.day\n",
        "clean_columns_mov_info['day_week'] = clean_columns_mov_info['theater_date'].dt.day_name()\n",
        "clean_columns_mov_info[['hours', 'time_unit']] = clean_columns_mov_info[\"runtime\"].apply(lambda x: pd.Series(str(x).split(\" \")))\n",
        "clean_columns_mov_info[[\"hours\"]] = clean_columns_mov_info[[\"hours\"]].apply(pd.to_numeric)/60\n",
        "clean_columns_mov_info"
      ],
      "metadata": {
        "id": "s9fRaKWfwdPw",
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 1000
        },
        "outputId": "e8f77e89-4dd7-448a-a7b4-a201c33ab6fd"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "<ipython-input-16-9c27a1aee98c>:4: SettingWithCopyWarning: \n",
            "A value is trying to be set on a copy of a slice from a DataFrame.\n",
            "Try using .loc[row_indexer,col_indexer] = value instead\n",
            "\n",
            "See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy\n",
            "  clean_columns_mov_info['month'] = clean_columns_mov_info['theater_date'].dt.month\n",
            "<ipython-input-16-9c27a1aee98c>:5: SettingWithCopyWarning: \n",
            "A value is trying to be set on a copy of a slice from a DataFrame.\n",
            "Try using .loc[row_indexer,col_indexer] = value instead\n",
            "\n",
            "See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy\n",
            "  clean_columns_mov_info['year'] = clean_columns_mov_info['theater_date'].dt.year\n",
            "<ipython-input-16-9c27a1aee98c>:6: SettingWithCopyWarning: \n",
            "A value is trying to be set on a copy of a slice from a DataFrame.\n",
            "Try using .loc[row_indexer,col_indexer] = value instead\n",
            "\n",
            "See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy\n",
            "  clean_columns_mov_info['date'] = clean_columns_mov_info['theater_date'].dt.day\n",
            "<ipython-input-16-9c27a1aee98c>:7: SettingWithCopyWarning: \n",
            "A value is trying to be set on a copy of a slice from a DataFrame.\n",
            "Try using .loc[row_indexer,col_indexer] = value instead\n",
            "\n",
            "See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy\n",
            "  clean_columns_mov_info['day_week'] = clean_columns_mov_info['theater_date'].dt.day_name()\n",
            "<ipython-input-16-9c27a1aee98c>:8: SettingWithCopyWarning: \n",
            "A value is trying to be set on a copy of a slice from a DataFrame.\n",
            "Try using .loc[row_indexer,col_indexer] = value instead\n",
            "\n",
            "See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy\n",
            "  clean_columns_mov_info[['hours', 'time_unit']] = clean_columns_mov_info[\"runtime\"].apply(lambda x: pd.Series(str(x).split(\" \")))\n",
            "<ipython-input-16-9c27a1aee98c>:8: SettingWithCopyWarning: \n",
            "A value is trying to be set on a copy of a slice from a DataFrame.\n",
            "Try using .loc[row_indexer,col_indexer] = value instead\n",
            "\n",
            "See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy\n",
            "  clean_columns_mov_info[['hours', 'time_unit']] = clean_columns_mov_info[\"runtime\"].apply(lambda x: pd.Series(str(x).split(\" \")))\n",
            "<ipython-input-16-9c27a1aee98c>:9: SettingWithCopyWarning: \n",
            "A value is trying to be set on a copy of a slice from a DataFrame.\n",
            "Try using .loc[row_indexer,col_indexer] = value instead\n",
            "\n",
            "See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy\n",
            "  clean_columns_mov_info[[\"hours\"]] = clean_columns_mov_info[[\"hours\"]].apply(pd.to_numeric)/60\n"
          ]
        },
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "     rating                                              genre      runtime  \\\n",
              "id                                                                            \n",
              "1         R                Action and Adventure|Classics|Drama  104 minutes   \n",
              "3         R                  Drama|Science Fiction and Fantasy  108 minutes   \n",
              "5         R                  Drama|Musical and Performing Arts  116 minutes   \n",
              "6         R                         Drama|Mystery and Suspense  128 minutes   \n",
              "8        PG                              Drama|Kids and Family   95 minutes   \n",
              "...     ...                                                ...          ...   \n",
              "1993     PG                                             Comedy   95 minutes   \n",
              "1995  PG-13                Action and Adventure|Comedy|Western  107 minutes   \n",
              "1997     PG                 Comedy|Science Fiction and Fantasy   88 minutes   \n",
              "1998      G  Classics|Comedy|Drama|Musical and Performing Arts  111 minutes   \n",
              "1999     PG    Comedy|Drama|Kids and Family|Sports and Fitness  101 minutes   \n",
              "\n",
              "                director theater_date  month  year  date   day_week     hours  \\\n",
              "id                                                                              \n",
              "1       William Friedkin   1971-10-09     10  1971     9   Saturday  1.733333   \n",
              "3       David Cronenberg   2012-08-17      8  2012    17     Friday  1.800000   \n",
              "5         Allison Anders   1996-09-13      9  1996    13     Friday  1.933333   \n",
              "6         Barry Levinson   1994-12-09     12  1994     9     Friday  2.133333   \n",
              "8            Jay Russell   2000-03-03      3  2000     3     Friday  1.583333   \n",
              "...                  ...          ...    ...   ...   ...        ...       ...   \n",
              "1993        James Lapine   1993-06-04      6  1993     4     Friday  1.583333   \n",
              "1995    Barry Sonnenfeld   1999-06-30      6  1999    30  Wednesday  1.783333   \n",
              "1997        Steve Barron   1993-07-23      7  1993    23     Friday  1.466667   \n",
              "1998      Gordon Douglas   1962-01-01      1  1962     1     Monday  1.850000   \n",
              "1999  David Mickey Evans   1993-04-01      4  1993     1   Thursday  1.683333   \n",
              "\n",
              "     time_unit  \n",
              "id              \n",
              "1      minutes  \n",
              "3      minutes  \n",
              "5      minutes  \n",
              "6      minutes  \n",
              "8      minutes  \n",
              "...        ...  \n",
              "1993   minutes  \n",
              "1995   minutes  \n",
              "1997   minutes  \n",
              "1998   minutes  \n",
              "1999   minutes  \n",
              "\n",
              "[1076 rows x 11 columns]"
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-8dbd7acd-49f7-4892-9131-44b81c1786a8\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>rating</th>\n",
              "      <th>genre</th>\n",
              "      <th>runtime</th>\n",
              "      <th>director</th>\n",
              "      <th>theater_date</th>\n",
              "      <th>month</th>\n",
              "      <th>year</th>\n",
              "      <th>date</th>\n",
              "      <th>day_week</th>\n",
              "      <th>hours</th>\n",
              "      <th>time_unit</th>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>id</th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>R</td>\n",
              "      <td>Action and Adventure|Classics|Drama</td>\n",
              "      <td>104 minutes</td>\n",
              "      <td>William Friedkin</td>\n",
              "      <td>1971-10-09</td>\n",
              "      <td>10</td>\n",
              "      <td>1971</td>\n",
              "      <td>9</td>\n",
              "      <td>Saturday</td>\n",
              "      <td>1.733333</td>\n",
              "      <td>minutes</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>R</td>\n",
              "      <td>Drama|Science Fiction and Fantasy</td>\n",
              "      <td>108 minutes</td>\n",
              "      <td>David Cronenberg</td>\n",
              "      <td>2012-08-17</td>\n",
              "      <td>8</td>\n",
              "      <td>2012</td>\n",
              "      <td>17</td>\n",
              "      <td>Friday</td>\n",
              "      <td>1.800000</td>\n",
              "      <td>minutes</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>5</th>\n",
              "      <td>R</td>\n",
              "      <td>Drama|Musical and Performing Arts</td>\n",
              "      <td>116 minutes</td>\n",
              "      <td>Allison Anders</td>\n",
              "      <td>1996-09-13</td>\n",
              "      <td>9</td>\n",
              "      <td>1996</td>\n",
              "      <td>13</td>\n",
              "      <td>Friday</td>\n",
              "      <td>1.933333</td>\n",
              "      <td>minutes</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>6</th>\n",
              "      <td>R</td>\n",
              "      <td>Drama|Mystery and Suspense</td>\n",
              "      <td>128 minutes</td>\n",
              "      <td>Barry Levinson</td>\n",
              "      <td>1994-12-09</td>\n",
              "      <td>12</td>\n",
              "      <td>1994</td>\n",
              "      <td>9</td>\n",
              "      <td>Friday</td>\n",
              "      <td>2.133333</td>\n",
              "      <td>minutes</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>8</th>\n",
              "      <td>PG</td>\n",
              "      <td>Drama|Kids and Family</td>\n",
              "      <td>95 minutes</td>\n",
              "      <td>Jay Russell</td>\n",
              "      <td>2000-03-03</td>\n",
              "      <td>3</td>\n",
              "      <td>2000</td>\n",
              "      <td>3</td>\n",
              "      <td>Friday</td>\n",
              "      <td>1.583333</td>\n",
              "      <td>minutes</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>...</th>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1993</th>\n",
              "      <td>PG</td>\n",
              "      <td>Comedy</td>\n",
              "      <td>95 minutes</td>\n",
              "      <td>James Lapine</td>\n",
              "      <td>1993-06-04</td>\n",
              "      <td>6</td>\n",
              "      <td>1993</td>\n",
              "      <td>4</td>\n",
              "      <td>Friday</td>\n",
              "      <td>1.583333</td>\n",
              "      <td>minutes</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1995</th>\n",
              "      <td>PG-13</td>\n",
              "      <td>Action and Adventure|Comedy|Western</td>\n",
              "      <td>107 minutes</td>\n",
              "      <td>Barry Sonnenfeld</td>\n",
              "      <td>1999-06-30</td>\n",
              "      <td>6</td>\n",
              "      <td>1999</td>\n",
              "      <td>30</td>\n",
              "      <td>Wednesday</td>\n",
              "      <td>1.783333</td>\n",
              "      <td>minutes</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1997</th>\n",
              "      <td>PG</td>\n",
              "      <td>Comedy|Science Fiction and Fantasy</td>\n",
              "      <td>88 minutes</td>\n",
              "      <td>Steve Barron</td>\n",
              "      <td>1993-07-23</td>\n",
              "      <td>7</td>\n",
              "      <td>1993</td>\n",
              "      <td>23</td>\n",
              "      <td>Friday</td>\n",
              "      <td>1.466667</td>\n",
              "      <td>minutes</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1998</th>\n",
              "      <td>G</td>\n",
              "      <td>Classics|Comedy|Drama|Musical and Performing Arts</td>\n",
              "      <td>111 minutes</td>\n",
              "      <td>Gordon Douglas</td>\n",
              "      <td>1962-01-01</td>\n",
              "      <td>1</td>\n",
              "      <td>1962</td>\n",
              "      <td>1</td>\n",
              "      <td>Monday</td>\n",
              "      <td>1.850000</td>\n",
              "      <td>minutes</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1999</th>\n",
              "      <td>PG</td>\n",
              "      <td>Comedy|Drama|Kids and Family|Sports and Fitness</td>\n",
              "      <td>101 minutes</td>\n",
              "      <td>David Mickey Evans</td>\n",
              "      <td>1993-04-01</td>\n",
              "      <td>4</td>\n",
              "      <td>1993</td>\n",
              "      <td>1</td>\n",
              "      <td>Thursday</td>\n",
              "      <td>1.683333</td>\n",
              "      <td>minutes</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "<p>1076 rows × 11 columns</p>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-8dbd7acd-49f7-4892-9131-44b81c1786a8')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-8dbd7acd-49f7-4892-9131-44b81c1786a8 button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-8dbd7acd-49f7-4892-9131-44b81c1786a8');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 16
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#clean_columns_mov_info.info()\n",
        "clean_columns_mov_info.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 237
        },
        "id": "IGB5Fy54_S5j",
        "outputId": "3f20f474-8a0f-4cc6-df75-8f370cb967c7"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "   rating                                genre      runtime          director  \\\n",
              "id                                                                              \n",
              "1       R  Action and Adventure|Classics|Drama  104 minutes  William Friedkin   \n",
              "3       R    Drama|Science Fiction and Fantasy  108 minutes  David Cronenberg   \n",
              "5       R    Drama|Musical and Performing Arts  116 minutes    Allison Anders   \n",
              "6       R           Drama|Mystery and Suspense  128 minutes    Barry Levinson   \n",
              "8      PG                Drama|Kids and Family   95 minutes       Jay Russell   \n",
              "\n",
              "   theater_date  month  year  date  day_week     hours time_unit  \n",
              "id                                                                \n",
              "1    1971-10-09     10  1971     9  Saturday  1.733333   minutes  \n",
              "3    2012-08-17      8  2012    17    Friday  1.800000   minutes  \n",
              "5    1996-09-13      9  1996    13    Friday  1.933333   minutes  \n",
              "6    1994-12-09     12  1994     9    Friday  2.133333   minutes  \n",
              "8    2000-03-03      3  2000     3    Friday  1.583333   minutes  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-4b549c04-d282-4c3c-9f94-fb0e66c2e68f\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>rating</th>\n",
              "      <th>genre</th>\n",
              "      <th>runtime</th>\n",
              "      <th>director</th>\n",
              "      <th>theater_date</th>\n",
              "      <th>month</th>\n",
              "      <th>year</th>\n",
              "      <th>date</th>\n",
              "      <th>day_week</th>\n",
              "      <th>hours</th>\n",
              "      <th>time_unit</th>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>id</th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>R</td>\n",
              "      <td>Action and Adventure|Classics|Drama</td>\n",
              "      <td>104 minutes</td>\n",
              "      <td>William Friedkin</td>\n",
              "      <td>1971-10-09</td>\n",
              "      <td>10</td>\n",
              "      <td>1971</td>\n",
              "      <td>9</td>\n",
              "      <td>Saturday</td>\n",
              "      <td>1.733333</td>\n",
              "      <td>minutes</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>R</td>\n",
              "      <td>Drama|Science Fiction and Fantasy</td>\n",
              "      <td>108 minutes</td>\n",
              "      <td>David Cronenberg</td>\n",
              "      <td>2012-08-17</td>\n",
              "      <td>8</td>\n",
              "      <td>2012</td>\n",
              "      <td>17</td>\n",
              "      <td>Friday</td>\n",
              "      <td>1.800000</td>\n",
              "      <td>minutes</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>5</th>\n",
              "      <td>R</td>\n",
              "      <td>Drama|Musical and Performing Arts</td>\n",
              "      <td>116 minutes</td>\n",
              "      <td>Allison Anders</td>\n",
              "      <td>1996-09-13</td>\n",
              "      <td>9</td>\n",
              "      <td>1996</td>\n",
              "      <td>13</td>\n",
              "      <td>Friday</td>\n",
              "      <td>1.933333</td>\n",
              "      <td>minutes</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>6</th>\n",
              "      <td>R</td>\n",
              "      <td>Drama|Mystery and Suspense</td>\n",
              "      <td>128 minutes</td>\n",
              "      <td>Barry Levinson</td>\n",
              "      <td>1994-12-09</td>\n",
              "      <td>12</td>\n",
              "      <td>1994</td>\n",
              "      <td>9</td>\n",
              "      <td>Friday</td>\n",
              "      <td>2.133333</td>\n",
              "      <td>minutes</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>8</th>\n",
              "      <td>PG</td>\n",
              "      <td>Drama|Kids and Family</td>\n",
              "      <td>95 minutes</td>\n",
              "      <td>Jay Russell</td>\n",
              "      <td>2000-03-03</td>\n",
              "      <td>3</td>\n",
              "      <td>2000</td>\n",
              "      <td>3</td>\n",
              "      <td>Friday</td>\n",
              "      <td>1.583333</td>\n",
              "      <td>minutes</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-4b549c04-d282-4c3c-9f94-fb0e66c2e68f')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-4b549c04-d282-4c3c-9f94-fb0e66c2e68f button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-4b549c04-d282-4c3c-9f94-fb0e66c2e68f');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 17
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#This gives a quick glance on the statistical measures of the numerical dataset\n",
        "# Average runtime for a movie is 1.7 hours or 106 minutes\n",
        "clean_columns_mov_info.describe()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 300
        },
        "id": "ewaGabf3Xnvl",
        "outputId": "f8374abb-8658-491c-df76-60e25a22f331"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "             month         year         date        hours\n",
              "count  1076.000000  1076.000000  1076.000000  1076.000000\n",
              "mean      6.506506  1991.498141    13.869888     1.771747\n",
              "std       3.638420    19.721526     9.382804     0.360515\n",
              "min       1.000000  1921.000000     1.000000     0.866667\n",
              "25%       3.000000  1983.000000     5.000000     1.550000\n",
              "50%       7.000000  1996.000000    13.000000     1.700000\n",
              "75%      10.000000  2006.000000    22.000000     1.933333\n",
              "max      12.000000  2018.000000    31.000000     5.966667"
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-81ae7dad-41b7-47bd-b8cc-1f65b1206cb3\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>month</th>\n",
              "      <th>year</th>\n",
              "      <th>date</th>\n",
              "      <th>hours</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>count</th>\n",
              "      <td>1076.000000</td>\n",
              "      <td>1076.000000</td>\n",
              "      <td>1076.000000</td>\n",
              "      <td>1076.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>mean</th>\n",
              "      <td>6.506506</td>\n",
              "      <td>1991.498141</td>\n",
              "      <td>13.869888</td>\n",
              "      <td>1.771747</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>std</th>\n",
              "      <td>3.638420</td>\n",
              "      <td>19.721526</td>\n",
              "      <td>9.382804</td>\n",
              "      <td>0.360515</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>min</th>\n",
              "      <td>1.000000</td>\n",
              "      <td>1921.000000</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.866667</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>25%</th>\n",
              "      <td>3.000000</td>\n",
              "      <td>1983.000000</td>\n",
              "      <td>5.000000</td>\n",
              "      <td>1.550000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>50%</th>\n",
              "      <td>7.000000</td>\n",
              "      <td>1996.000000</td>\n",
              "      <td>13.000000</td>\n",
              "      <td>1.700000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>75%</th>\n",
              "      <td>10.000000</td>\n",
              "      <td>2006.000000</td>\n",
              "      <td>22.000000</td>\n",
              "      <td>1.933333</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>max</th>\n",
              "      <td>12.000000</td>\n",
              "      <td>2018.000000</td>\n",
              "      <td>31.000000</td>\n",
              "      <td>5.966667</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-81ae7dad-41b7-47bd-b8cc-1f65b1206cb3')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-81ae7dad-41b7-47bd-b8cc-1f65b1206cb3 button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-81ae7dad-41b7-47bd-b8cc-1f65b1206cb3');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 18
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "top_director = clean_columns_mov_info[\"director\"].unique()[:3]\n",
        "top_genre = clean_columns_mov_info[\"genre\"].unique()[:10]\n",
        "top_director_counts = clean_columns_mov_info[\"director\"].value_counts().nlargest(10).tolist()\n",
        "\n",
        "active_years = clean_columns_mov_info[\"year\"].value_counts().nlargest(10)\n",
        "\n"
      ],
      "metadata": {
        "id": "MqeNN8shHaAi"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "#movie_rating = movie_information.pivot(index='synopsis', columns='director', values='currency')\n",
        "#movie_rating.head()"
      ],
      "metadata": {
        "id": "HgKN7opuj0-R"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Analysis"
      ],
      "metadata": {
        "id": "cIDQACDkjkWd"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "#Plot a histogram showing movie releases by months. understand the best time.\n",
        "#Data is consistent with the industry norm.It is a common practice that Friday is reserved as the day for movie theaters to premiere new \n",
        "#films due to the fact that many people want to watch the movie during their weekends\n",
        "sns.histplot(data = clean_columns_mov_info, x =\"day_week\",color =\"pink\",bins=10).set_title('Best day of the Week to premiere a Movie in Theaters')\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 489
        },
        "id": "wjXnUSDJIwVi",
        "outputId": "9066062e-77fb-4486-b1f9-472a91023da7"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "Text(0.5, 1.0, 'Best day of the Week to premiere a Movie in Theaters')"
            ]
          },
          "metadata": {},
          "execution_count": 69
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "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0iUREdm9e7eYmZmJv7+/zJs3TxYsWCB169YVMzMzOXz4sDKvgo6zZs2aia2trUycOFG+/vpr+fjjj6V169ayb9++Qq+70sawU0ZyPgyffGm1WomIiNCr++uvvwoAiYyM1Cvftm2bXvnGjRsFgMTExOQ731u3bgkAmTJlSqHaOWrUKAGgt5MnJCSIra1troM4LS0t1/hvv/22WFpayoMHD5Qyf39/adKkiV69DRs2CADZu3dvge2pV6+eODs7y507d5SyP/74Q4yMjGTgwIFK2d69ewWArF+//qnLuH79+nzn7enpKQBk//79SllCQoJotVp59913lbIZM2aIlZWV/Pnnn3rjf/DBB2JsbCyxsbEFtmHs2LECQP755x8REVmzZo2Ym5tLenq6bNmyRYyNjZUv0y+//FIAyIEDB4o078LuRznLnRN2PvvsM9FoNDJjxowClyFH7dq19b6McuTsS7/++qtSdv/+ffHy8pIqVapIVlZWgdPNOUaOHj2qlP39999ibm4u//3vf5WynA/hfv366Y1/9epVMTY2lo8++kiv/NSpU2JiYqJXHhAQIABk9erVStn58+cFgBgZGcmhQ4eU8u3btwsACQ8PV8qeDDv3798XOzs7GTp0qN684+LixNbWVq88KChIAMgHH3ygV7co2y8veR2fa9asybV/5+XxsHP69Gm97RgWFibW1taSmpqaK+wkJCSImZmZdOjQQW/75uzD3377rYiIZGdnS6VKlaRnz5568/3uu+9yte/JsLNy5UoxMjLS269ERJYsWaJ3nOQnv7Dj6Ogod+/eVcp/+uknASCbNm0qcHqPK0zYKcx82rZtK3Xq1NH7HM3OzpZmzZpJ9erVlbIHDx7kOo6uXLkiWq1Wpk+frpTFxMTk2mdzplm9enUJDAzUC8BpaWni5eUl7du3V8ryO87u3bun7CvlGS9jlbGwsDDs3LkTO3fuxKpVq9C6dWsMGTIEGzZsUOqsX78etra2aN++PW7fvq28/Pz8YG1tjb179wL4//4pmzdvRmZmZom0b8uWLWjatCkaN26slFWoUEE5rf44CwsL5e/79+/j9u3beOWVV5CWlobz588rwwYOHIjDhw/j0qVLSllkZCTc3d2Vy095uXnzJk6cOIHg4GC90+V169ZF+/btsWXLlmIvZ0F8fX3xyiuvKO8rVKiAmjVr4vLly0rZ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qRrDDhEREakaww4RERGpGsMOERERqRrDDhEREakaww4RERGpGsMOERERqRrDDhEREakaww4RERGpGsMOERERqRrDDhEREakaww4RERGpGsMOERERqRrDDhEREakaww4RERGpGsMOERERqRrDDhEREakaww4RERGpGsMOERERqRrDDhEREakaww4RERGpGsMOERERqRrDDhEREakaww4RERGpGsMOERERqRrDDhEREakaww4RERGpGsMOERERqRrDDhEREakaww4RERGpGsMOERERqRrDDhEREakaww4RERGpGsMOERERqRrDDhEREakaww4RERGpGsMOERERqRrDDhEREakaww4RERGpGsMOERERqRrDDhEREakaww4RERGpGsMOERERqVq5CTuffPIJNBoNRo0apZQ9ePAAISEhcHR0hLW1NXr27In4+Hi98WJjY9GlSxdYWlrC2dkZY8eOxcOHD8u49URERFRelYuwExMTg6+++gp169bVKx89ejQ2bdqE9evXY9++fbhx4wZeffVVZXhWVha6dOmCjIwMHDx4EMuXL0dERAQmT55c1otARERE5ZTBw05KSgr69++PZcuWwd7eXilPSkrCN998g/nz56NNmzbw8/NDeHg4Dh48iEOHDgEAduzYgbNnz2LVqlWoV68eOnXqhBkzZiAsLAwZGRmGWiQiIiIqRwwedkJCQtClSxe0a9dOr/zYsWPIzMzUK69VqxY8PDwQHR0NAIiOjkadOnXg4uKi1AkMDERycjLOnDmT7zzT09ORnJys9yIiIiJ1MjHkzNeuXYvjx48jJiYm17C4uDiYmZnBzs5Or9zFxQVxcXFKnceDTs7wnGH5mTVrFqZNm/aMrSciIqLngcHO7Fy7dg0jR45EZGQkzM3Ny3Te48ePR1JSkvK6du1amc6fiIiIyo7Bws6xY8eQkJCABg0awMTEBCYmJti3bx8+//xzmJiYwMXFBRkZGUhMTNQbLz4+Hq6urgAAV1fXXHdn5bzPqZMXrVYLnU6n9yIiIiJ1MljYadu2LU6dOoUTJ04or4YNG6J///7K36ampti9e7cyzoULFxAbGwt/f38AgL+/P06dOoWEhASlzs6dO6HT6eDr61vmy0RERETlj8H67NjY2OCll17SK7OysoKjo6NSPnjwYIwZMwYODg7Q6XQYPnw4/P390bRpUwBAhw4d4OvriwEDBmDOnDmIi4vDxIkTERISAq1WW+bLREREROWPQTsoP82CBQtgZGSEnj17Ij09HYGBgVi0aJEy3NjYGJs3b8awYcPg7+8PKysrBAUFYfr06QZsNREREZUn5SrsREVF6b03NzdHWFgYwsLC8h3H09MTW7ZsKeWWERER0fPK4M/ZISIiIipNDDtERESkagw7REREpGoMO0RERKRqDDtERESkagw7REREpGoMO0RERKRqDDtERESkagw7REREpGoMO0RERKRqDDtERESkagw7REREpGoMO0RERKRqDDtERESkagw7REREpGoMO0RERKRqDDtERESkagw7REREpGrFCjtVq1bFnTt3cpUnJiaiatWqz9woIiIiopJSrLBz9epVZGVl5SpPT0/H9evXn7lRRERERCXFpCiVf/75Z+Xv7du3w9bWVnmflZWF3bt3o0qVKiXWOCIiIqJnVaSw06NHDwCARqNBUFCQ3jBTU1NUqVIF8+bNK7HGERERET2rIoWd7OxsAICXlxdiYmLg5ORUKo0iIiIiKilFCjs5rly5UtLtICIiIioVxQo7ALB7927s3r0bCQkJyhmfHN9+++0zN4yIiIioJBQr7EybNg3Tp09Hw4YNUbFiRWg0mpJuFxEREVGJKFbYWbJkCSIiIjBgwICSbg8RERFRiSrWc3YyMjLQrFmzkm4LERERUYkrVtgZMmQIVq9eXdJtISIiIipxxbqM9eDBAyxduhS7du1C3bp1YWpqqjd8/vz5JdI4IiIiomdVrLBz8uRJ1KtXDwBw+vRpvWHsrExERETlSbHCzt69e0u6HURERESlolh9doiIiIieF8U6s9O6desCL1ft2bOn2A0iIiIiKknFCjs5/XVyZGZm4sSJEzh9+nSuHwglIiIiMqRihZ0FCxbkWT516lSkpKQ8U4OIiIiISlKJ9tl54403+LtYREREVK6UaNiJjo6Gubl5SU6SiIiI6JkU6zLWq6++qvdeRHDz5k0cPXoUkyZNKpGGEREREZWEYoUdW1tbvfdGRkaoWbMmpk+fjg4dOpRIw4iIiIhKQrHCTnh4eEm3g4iIiKhUFCvs5Dh27BjOnTsHAKhduzbq169fIo0iIiIiKinFCjsJCQno27cvoqKiYGdnBwBITExE69atsXbtWlSoUKEk20hERERUbMW6G2v48OG4f/8+zpw5g7t37+Lu3bs4ffo0kpOTMWLEiJJuIxEREVGxFevMzrZt27Br1y74+PgoZb6+vggLC2MHZSIiIipXinVmJzs7G6amprnKTU1NkZ2d/cyNIiIiIiopxQo7bdq0wciRI3Hjxg2l7Pr16xg9ejTatm1b6OksXrwYdevWhU6ng06ng7+/P7Zu3aoMf/DgAUJCQuDo6Ahra2v07NkT8fHxetOIjY1Fly5dYGlpCWdnZ4wdOxYPHz4szmIRERGRChUr7Hz55ZdITk5GlSpV4O3tDW9vb3h5eSE5ORlffPFFoadTuXJlfPLJJzh27BiOHj2KNm3aoHv37jhz5gwAYPTo0di0aRPWr1+Pffv24caNG3oPNMzKykKXLl2QkZGBgwcPYvny5YiIiMDkyZOLs1hERESkQsXqs+Pu7o7jx49j165dOH/+PADAx8cH7dq1K9J0unXrpvf+o48+wuLFi3Ho0CFUrlwZ33zzDVavXo02bdoAePR8Hx8fHxw6dAhNmzbFjh07cPbsWezatQsuLi6oV68eZsyYgXHjxmHq1KkwMzMrzuIRERGRihTpzM6ePXvg6+uL5ORkaDQatG/fHsOHD8fw4cPRqFEj1K5dG7/++muxGpKVlYW1a9ciNTUV/v7+OHbsGDIzM/UCVK1ateDh4YHo6GgAj36Lq06dOnBxcVHqBAYGIjk5WTk7lJf09HQkJyfrvYiIiEidihR2Fi5ciKFDh0Kn0+UaZmtri7fffhvz588vUgNOnToFa2traLVavPPOO9i4cSN8fX0RFxcHMzMz5Tk+OVxcXBAXFwcAiIuL0ws6OcNzhuVn1qxZsLW1VV7u7u5FajMRERE9P4oUdv744w907Ngx3+EdOnTAsWPHitSAmjVr4sSJEzh8+DCGDRuGoKAgnD17tkjTKKrx48cjKSlJeV27dq1U50dERESGU6Q+O/Hx8Xnecq5MzMQEt27dKlIDzMzMUK1aNQCAn58fYmJi8Nlnn6FPnz7IyMhAYmKi3tmd+Ph4uLq6AgBcXV1x5MiRXG3MGZYfrVYLrVZbpHYSERHR86lIZ3YqVaqE06dP5zv85MmTqFix4jM1KDs7G+np6fDz84OpqSl2796tDLtw4QJiY2Ph7+8PAPD398epU6eQkJCg1Nm5cyd0Oh18fX2fqR1ERESkDkU6s9O5c2dMmjQJHTt2hLm5ud6wf//9F1OmTEHXrl0LPb3x48ejU6dO8PDwwP3797F69WpERUVh+/btsLW1xeDBgzFmzBg4ODhAp9Nh+PDh8Pf3R9OmTQE8umzm6+uLAQMGYM6cOYiLi8PEiRMREhLCMzdEREQEoIhhZ+LEidiwYQNq1KiB0NBQ1KxZEwBw/vx5hIWFISsrCxMmTCj09BISEjBw4EDcvHkTtra2qFu3LrZv34727dsDABYsWAAjIyP07NkT6enpCAwMxKJFi5TxjY2NsXnzZgwbNgz+/v6wsrJCUFAQpk+fXpTFIiIiIhUrUthxcXHBwYMHMWzYMIwfPx4iAgDQaDQIDAxEWFhYrrujCvLNN98UONzc3BxhYWEICwvLt46npye2bNlS6HkSERHRi6XIDxXMCRf37t3DX3/9BRFB9erVYW9vXxrtIyIiInomxXqCMgDY29ujUaNGJdkWIiIiohJXrN/GIiIiInpeMOwQERGRqjHsEBERkaox7BAREZGqMewQERGRqjHsEBERkaox7BAREZGqMewQERGRqjHsEBERkaox7BAREZGqMewQERGRqjHsEBERkaox7BAREZGqMewQERGRqjHsEBERkaox7BAREZGqMewQERGRqjHsEBERkaox7BAREZGqMewQERGRqjHsEBERkaox7BAREZGqMewQERGRqjHsEBERkaox7BAREZGqMewQERGRqjHsEBERkaox7BAREZGqMewQERGRqjHsEBERkaox7BAREZGqMewQERGRqjHsEBERkaox7BAREZGqMewQERGRqjHsEBERkaox7BAREZGqMewQERGRqjHsEBERkaox7BAREZGqMewQERGRqjHsEBERkaox7BAREZGqMewQERGRqhk07MyaNQuNGjWCjY0NnJ2d0aNHD1y4cEGvzoMHDxASEgJHR0dYW1ujZ8+eiI+P16sTGxuLLl26wNLSEs7Ozhg7diwePnxYlotCRERE5ZRBw86+ffsQEhKCQ4cOYefOncjMzESHDh2Qmpqq1Bk9ejQ2bdqE9evXY9++fbhx4wZeffVVZXhWVha6dOmCjIwMHDx4EMuXL0dERAQmT55siEUiIiKicsbEkDPftm2b3vuIiAg4Ozvj2LFjaNmyJZKSkvDNN99g9erVaNOmDQAgPDwcPj4+OHToEJo2bYodO3bg7Nmz2LVrF1xcXFCvXj3MmDED48aNw9SpU2FmZmaIRSMi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\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#Top Movie Genre\n",
        "top_genre = clean_columns_mov_info[\"genre\"].unique()[:10]\n",
        "\n",
        "top_genre_counts = clean_columns_mov_info[\"genre\"].value_counts().nlargest(10).tolist()\n",
        "\n",
        "print(\"Genre:\", top_genre)\n",
        "print(\"Counts:\", top_genre_counts)"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "ZyYK-JBI0B3p",
        "outputId": "5e3b2aaf-b7fb-4bad-a554-913240732561"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Genre: ['Action and Adventure|Classics|Drama' 'Drama|Science Fiction and Fantasy'\n",
            " 'Drama|Musical and Performing Arts' 'Drama|Mystery and Suspense'\n",
            " 'Drama|Kids and Family' 'Comedy' 'Drama'\n",
            " 'Action and Adventure|Mystery and Suspense|Science Fiction and Fantasy'\n",
            " 'Classics|Comedy|Drama' 'Comedy|Drama|Mystery and Suspense']\n",
            "Counts: [95, 83, 58, 48, 32, 29, 26, 25, 24, 23]\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#Filter the top movie genres\n",
        "y= top_genre\n",
        " \n",
        "# getting values against each value of y\n",
        "x= top_genre_counts\n",
        "plt.barh(y, x , color = 'red' , alpha =0.75)\n",
        "\n",
        " \n",
        "# setting label of y-axis\n",
        "plt.ylabel(\"Top 10 movie genre\")\n",
        " \n",
        "# setting label of x-axis\n",
        "plt.xlabel(\"Counts\")\n",
        "plt.title(\"Top 10 Movie Genre\")\n",
        "plt.show()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 472
        },
        "id": "Jlq6HDN-3Ues",
        "outputId": "d595266d-3953-4910-b919-acdb37169107"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "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Wrw7RY0aNXD48GGcP38e1tbWGDp0KHx9faUWz/wa1atXR1RUFLKystC+fXtYWVnBz88PmpqaYmJh4cKFaNmyJVxdXeHo6IgWLVqgUaNGudoyMTFB8+bNYW5uLrUGREFmzJgBPT091KlTB/369cPr168RHh6OSZMmFbrvkiVLULlyZTRv3hyurq5wcnKCjY2NbB2Qh2nTpsHGxgZOTk6wt7eHrq5uoaMuiIiI6MciEb52FTIiIqISlJiYCCMjo69eLPN7JggCTExMMGzYMIwdO1ZqW3k+77ykpqZCQ0MDr1u0gLoCb6pVLkVElHYERERUzMTv79evC12fid/uRERE/6GnT59i+/btePz4MQYMGFDa4RARERGVKCYdiIiI/kPVqlVD1apVsXr1alSuXLm0wyEiIiIqUUw6EBHRd0lTUxMzZ84s7TCKXWHTJsrreRMREdGPiWs6EBERUanhmg4/AK7pQERU7siypgPvXkFEREREREREJYJJByIiIiIiIiIqEUw6EBEREREREVGJ4ORJIiIiKn2HDgGFzAklIiKisocjHYiIiIiIiIioRDDpQEREREREREQlgkkHIiIiIiIiIioRTDoQERERERERUYlg0oGIiIiIiIiISgTvXkFERESlz8UFUOB/S34YERGlHQEREf1HONKBiIiIiIiIiEoEkw5EREREREREVCKYdCAiIiIiIiKiEsGkAxERERERERGVCCYdiIiIiIiIiKhEMOlARERERERERCWCSQciIiIiIiIiKhFMOhARERERERFRiSiXSYfg4GBoamqWdhhfzd/fHw0aNCiRtiUSCfbt21cibX9PDA0NERkZWdphlDve3t5wc3Mr7TDKBH9/f3h7exdrm2X977c4Ppv5+U5ERERUtnwXSYezZ89CXl4eLi4uMu9raGiIZcuWSZV5eHjg9u3bxRTd983JyQny8vK4cOFCaYeSr+/hQtXb2xsSiQRDhw7NtW348OGQSCTFdoFY1i+KvtWaNWtgbW0NVVVVaGpqomHDhvjtt99KO6zvwrf2TXJyMjp06FCCEX67yMhISCSSXI9p06bJ/Nn8I36+JyYm5tl/ffv2Ldb2r1y5UiztERERERVGobQDAIB169Zh5MiRWLduHR49eoTq1at/U3tKSkpQUlIqpui+X0lJSThz5gxGjBiB9evXo0mTJqUdUonKysqCRCKB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ODo6QkNDA4mJiRg0aBC0tLSwd+9eJCUlYePGjSURJxERERERERGVMTKPdBg7diy8vb1x584dVKpUSSzv2LEjTp06VazBEREREREREVHZJXPS4cKFCxgyZEiu8ho1auDx48fFEhQRERERERERlX0yJx0UFRWRmpqaq/z27dvQ1tYulqCIiIiIiIiIqOyTOenQuXNnzJo1CxkZGQAAiUSCpKQkTJo0Cd27dy/2AImIiIiIiIiobJIIgiDIssPr16/Ro0cPXLx4EW/evEH16tXx+PFj2Nra4vDhw1BRUSmpWImIiKickeU+30RERPR9kOX7W+a7V2hoaCAsLAynT5/G1atXkZaWBhsbGzg6On51wERERERERERU/sg80oGIiIiouHCkAxERUdlToiMdAgMD8yyXSCSoVKkS6tSpg1atWkFeXl7WpomIiIiIiIioHJE56bB06VI8ffoU7969Q+XKlQEAL1++hLKyMlRVVZGSkgJjY2NERETAwMCg2AMmIiIiIiIiorJB5rtXzJ07F02aNMGdO3fw/PlzPH/+HLdv30azZs2wfPlyJCUlQVdXF2PGjCmJeImIiIiIiIiojJB5TYfatWtjz549aNCggVR5TEwMunfvjnv37uHMmTPo3r07kpOTizNWIiIiKme4pgMREVHZU6JrOiQnJyMzMzNXeWZmJh4/fgwAqF69Ot68eSNr00RERPSjcnEBFGT+bwnRJxERpR0BERHlQ+bpFQ4ODhgyZAhiYmLEspiYGPz8889o06YNAODatWswMjIqviiJiIiIiIiIqMyROemwbt06aGlpoVGjRlBUVISioiIaN24MLS0trFu3DgCgqqqKxYsXF3uwRERERERERFR2yDyOUVdXF2FhYbh16xZu3boFADAzM4OZmZlYx8HBofgiJCIiIiIiIqIy6asnT36ZaCAiIiIiIiIi+pzM0yuIiIiIiIiIiIqCSQciIiIiIiIiKhFMOhARERERERFRiWDSgYiIiIrM398fDRo0KO0wiIiIqIz4qqTD33//jb59+8LW1hYPHz4EAGzatAmnT58u1uCIiIh+BI8fP8bIkSNhbGwMRUVFGBgYwNXVFeHh4aUdGhEREdE3kTnpsGfPHjg5OUFJSQkxMTFIT08HALx+/Rpz584t9gCJiIjKs8TERDRq1AgnTpzAwoULce3aNRw5cgQODg4YPnx4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Q/grVqzIiRMn+Pnnn/nll18IDg4mICCARYsWZWrL2tr6ofGEhYURHR3NuHHjKF26NNbW1rz//vsmjx88Srt27bhw4QITJkygePHiWFlZUa1atUxtPOzYPo0+ffrQvn177OzscHFxMSalrly5QqVKlZg3b16mdQoUKGD8+f7z52lYW1tnOenkvfuesTyrsocdD3McvzVr1vDHH3/QsmVLk/LU1FRiYmKoW7eusexxjpOFhQXR0dFs3bqVtWvXMmnSJAYOHMj27dsz/d5aWVm9VhOeioiIvO400kFEXnjr1q1j3759NG/e/KH1MobAd+3alQoVKlC6dGmTO9tPauvWrRQvXpyBAwfi7++Ph4dHls++P8wHH3zAvn37KFeuHD4+PlnWKVCgAMnJycbvR48e5dq1ayZ1HBwcaNmyJdOnT2fhwoUsXrzYOD/Cvfz8/IiPj89yGdw9Vu3bt6dp06b4+vri6ur62BM43ttGjx49aNCgAWXLlsXKyoq//vorW214e3tnSsL8+uuvj7XuG2+8QenSpTO9ZaJixYocPXqUggULUrp0aZNPdl+B6e3tzZ07d0wSVxcuXODw4cMP7MfnqWTJkuTJk4e4uDhjWUpKyiNfuzlz5kxatWpFfHy8yadVq1ZZTih5r4zRIampqSblBoOBGjVqMGTIEPbs2YOlpSVLly59wj0TERGRV4WSDiLyQrl58yZnzpzhjz/+YPfu3YwcOZKgoCAaNWpEaGjoQ9f18PBg586drFmzhiNHjhAeHm5yMfakPDw8SEpKYsGCBRw7doyJEydm+2IqX758JCcnExMT88A677zzDl999RV79uxh586ddOnSxeQu9/jx4/nuu+84dOgQR44c4YcffsDV1dXkbQcZWrdujaurK02aNCE2Npbjx4+zePFitm3bZtynJUuWEB8fT0JCAh988EG27557eHgwd+5cEhMT2b59OyEhIY8cYXG/Ll26cPToUfr06cPhw4eZP39+pleMZldISAhvvPEGQUFBbN68mRMnTrBhwwZ69OhhMjno4/Dw8CAoKIiPPvqILVu2kJCQQJs2bShSpAhBQUFPFeezYG9vT7t27ejTpw/r16/nwIEDdOzYkVy5cj3wdZ/nz5/nxx9/pF27dpQrV87kExoayrJlyx6YrAIoXrw4BoOBlStXcv78ea5cucL27dsZOXIkO3fuJCkpiSVLlnD+/Hm8vb3NtesiIiLyklDSQUReKKtXr6ZQoUK4u7tTr1491q9fz8SJE1m+fDkWFhYPXbdz5840a9aMli1bUrVqVS5cuEDXrl2fOqb33nuPXr160b17d9588022bt1KeHh4tttxcnJ66FD1yMhI3NzceOutt/jggw8ICwvDxsbGuNze3p6xY8fi7+9P5cqVOXnyJD/99JPJ/BQZLC0tWbt2LQULFqRBgwb4+voyevRo4zEcP348+fLlo3r16jRu3JjAwEAqVqyYrf2ZOXMmFy9epGLFirRt25YePXpkeg3ooxQrVozFixezbNkyypcvz7Rp0xg5cmS22rifjY0NmzZtolixYjRr1gxvb286duzIjRs3cHBwyHZ7UVFRVKpUiUaNGlGtWjXS09P56aefMj32kFPGjx9PtWrVaNSoEQEBAdSoUQNvb2/y5s2bZf1vvvkGW1tb48ST96pTpw7W1tZ8++23D9xekSJFGDJkCP3798fFxYXu3bvj4ODApk2baNCgAZ6engwaNIjIyEjq16//zPZTREREXk6G9Ie9p0tERB6bwWDgxIkTD3yNpcjzcPXqVYoUKUJkZCQdO3bM6XAe6fLlyzg6OpLy73/j8AQTrIqIPLX163M6ApGXjvHvd0rKI2/q6K+7iIjIS2zPnj0cOnSIKlWqkJKSwtChQwFeiMc/RERERJR0EBERecmNGzeOw4cPY2lpSaVKldi8eTNvvPFGToclIiIioqSDiMizMnjw4CwndRQxpwoVKrBr166cDkNEREQkS0o6iIg8IxERETkdgoiIiIjIC0VvrxARERERERERs1DSQURERERERETMQo9XiIiISM5btQoe8cotEREReflopIOIiIiIiIiImIWSDiIiIiIiIiJiFko6iIiIiIiIiIhZKOkgIiIiIiIiImahpIOIiIiIiIiImIWSDiIiIiIiIiJiFnplpoiIiOS8hg0ht/5bIiIiZrZ+fU5H8NrRSAcRERERERERMQslHURERERERETELJR0EBERERERERGzUNJBRERERERERMxCSQcRERERERERMQslHURERERERETELJR0EBERERERERGzUNJBRERERERERMxCSQcRETMwGAycPHnymbUXERHBm2+++czaywnu7u58+eWXOd5GTjIYDCxbtiynwxARERF5bpR0EJEXUvv27TEYDBgM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fHzo27ev8S589erV6dKlCy1btqRAgQKMHTs20/oGg4Hly5eTL18+3n77bQICAihZsiQLFy58qrgGDRpExYoVCQwMpFatWsZkUHbkypWLpUuXcv36dapUqUKnTp0YMWLEE8dUvnx5xo8fz5gxYyhXrhzz5s1j1KhR2W7no48+okyZMvj7+1OgQAFiY2MfeU5bWFhw4cIFQkND8fT0JDg4mPr162caIdOxY0du3bpFhw4dnng/RURE5NWjt1eIiJjB/W+vEHnVzZ07l169evHnn3+avL3kUYyzX+vtFSIi8jzo7RXPhN5eISIiIs/FtWvXSE5OZvTo0XTu3DlbCQcRERF59enxChEREXliY8eOxcvLC1dXVwYMGJDT4YiIiMgLRkkHEREzGDx4ME5OTjkdhojZRUREcPv2bWJiYrCzs8vpcEREROQFo8crRETMICIiIqdDEBERERHJcRrpICIiIiIiIiJmoaSDiIiIiIiIiJiFkg4iIiIiIiIiYhaa00FERERy3qpV8Ij3fIuIiMjLRyMdRERERERERMQslHQQEREREREREbNQ0kFEREREREREzEJJBxERERERERExCyUdRERERERERMQs9PYKERERyXkNG0Ju/bdERETkmVq/Pqcj0EgHERERERERETEPJR1ERERERERExCyUdBARERERERERs1DSQURERERERETMQkkHERERERERETELJR1ERERERERExCyUdBARERERERERs1DSQURERERERETMQkkHEXkpzJ49Gycnp5wO44lFRETw5ptvmqVtg8HAsmXLzNL2i8Td3Z0NGzZke73ndXw2bNiAwWDg0qVLT93WyZMnMRgMTx+UiIiISA5T0kFEzGLbtm1YWFjQsGHDbK/r7u7Ol19+aVLWsmVLjhw58oyie7EFBgZiYWFBXFxcTofyQO3bt6dJkyY5HQZnzpzh448/pmTJklhZWeHm5kbjxo2JiYl57rFUr16d5ORkHB0dzdK+u7s7BoMBg8GAtbU17u7uBAcHs27dOrNsT0RERORZUNJBRMxi5syZfPzxx2zatIk///zzqduztramYMGCzyCyF1tSUhJbt26le/fuzJo1K6fDMbvU1FTS0tKeaN2TJ09SqVIl1q1bxxdffMG+fftYvXo1tWvXplu3bs840keztLTE1dXVrCMUhg4dSnJyMocPH+abb77B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okyZMvj7+1OgQAFiY2PJkycP3333HYcOHcLPz48xY8YwfPjwx2rvSWIqWbIku3fvpnbt2nz66aeUK1eOunXrEhMTw9SpU7Nc57333qNXr150796dN998k61btxIeHm5cbmFhwYULFwgNDcXT05Pg4GDq169vnPgwNTWVbt264e3tTb169fD09Hzgm0k8PT1Zu3YtCQkJVKlShWrVqrF8+XJy586Ng4MDmzZtokGDBnh6ejJo0CAiIyNNJgXNyueff06hQoUoXbo0bdu2JSUlhZiYmExvMcnK+PHjyZcvH9WrV6dx48YEBgZSsWLFR673KIMGDaJixYoEBgZSq1YtXF1dHznqQkRERF4fhvSnmY1LRETkOXF3d2f27NlPlVh6WZw8eZISJUo81YSZL4vLly/j6OhIyr//jUNuDcAUERF5pu57nfyzYvz7nZLyyPmZNNJBRERERERERMxCSQcRERERERERMQslHURE5KXQs2dP3N3dczqM58LJyYnBgwfndBgiIiIiT01zOoiIiEiO0ZwOIiIiZqQ5HURERERERETkVaWkg4iIiIiIiIiYhZIOIiIiIiIiImIWenhSREREct6qVfCIZ0JFRETk5aORDiIiIiIiIiJiFko6iIiIiIiIiIhZKOkgIiIiIiIiImahpIOIiIiIiIiImIWSDiIiIiIiIiJiFko6iIiIiIiIiIhZKOkgIiIiIiIiImahpIOIiIiIiIiImIWSDiIiIiIiIiJiFko6iIiIiIiIiIhZKOkgIiIiIiIiImahpIOIiIiIiIiImIWSDiIiIiIiIiJiFko6iIiIiIiIiIhZKOkgIiIiIiIiImaRO6cDEBERkddXeno6AJcvX87hSERERORxZfzdzvg7/jBKOoiIiEiOuXDhAgBubm45HImIiIhk1z///IOjo+ND6yjpICIiIjnG2dkZgKSkpEf+p0XM7/Lly7i5uXH69GkcHBxyOpzXmvrixaL+eHGoL14M6enp/PPPPxQuXPiRdZV0EBERkRyTK9fd6aUcHR31n8cXiIODg/rjBaG+eLGoP14c6ouc97g3CzSRpIiIiIiIiIiYhZIOIiIiIiIiImIWSjqIiIhIjrGysmLw4MFYWVnldCiC+uNFor54sag/Xhzqi5ePIf1x3nEhIiIiIiIiIpJNGukgIiIiIiIiImahpIOIiIiIiIiImIWSDiIi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\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#sns.pairplot(data = clean_columns_mov_info)\n",
        "sns.countplot(x=\"month\", data=clean_columns_mov_info)#hue=\"year\","
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 466
        },
        "id": "iqMFjgS3WP5n",
        "outputId": "cfd1aece-47a4-4e15-e7af-79b8716ab9c3"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "<Axes: xlabel='month', ylabel='count'>"
            ]
          },
          "metadata": {},
          "execution_count": 24
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "iVBORw0KGgoAAAANSUhEUgAAAjsAAAGwCAYAAABPSaTdAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjcuMSwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy/bCgiHAAAACXBIWXMAAA9hAAAPYQGoP6dpAAArvElEQVR4nO3df1yV9cH/8fcBBJnxI0g4nASlcmnmr7Ic6t3tlIemzukyyx7knDrdDH8Qu9W4F1pmkW41ZzPI7rLVdK1VWrmlERr2AxEhuvvhTJszph3oeyscwUCE6/vHHp3tDNDCA9fh0+v5eFyPh9fnuq6P70MGb67rOtdxWJZlCQAAwFBBdgcAAADoSJQdAABgNMoOAAAwGmUHAAAYjbIDAACMRtkBAABGo+wAAACjhdgdIBA0Nzfr+PHjioiIkMPhsDsOAAD4CizL0qlTp+RyuRQU1Pb5G8qOpOPHjysxMdHuGAAAoB0qKirUq1evNrdTdiRFRERI+scXKzIy0uY0AADgq/B4PEpMTPT+HG8LZUfyXrqKjIyk7AAA0MWc7xYUblAGAABGo+wAAACjUXYAAIDRKDsAAMBolB0AAGA0yg4AADAaZQcAABiNsgMAAIxG2QEAAEaj7AAAAKNRdgAAgNEoOwAAwGiUHQAAYDTKDgAAMBplBwAAGC3E7gCB6vPc39kdQT0X3G53BAAAujzO7AAAAKNRdgAAgNEoOwAAwGiUHQAAYDTKDgAAMBplBwAAGI2yAwAAjEbZAQAARqPsAAAAo1F2AACA0Sg7AADAaJQdAABgNMoOAAAwGmUHAAAYzdays2fPHk2ePFkul0sOh0Pbtm1rc9+f/vSncjgcWrdunc/4iRMnlJaWpsjISEVHR2vu3Lmqra3t2OAAAKDLsLXs1NXVafDgwdqwYcM599u6dav27t0rl8vVYltaWpo+/PBD5efna/v27dqzZ4/mz5/fUZEBAEAXE2LnXz5hwgRNmDDhnPscO3ZMixYt0s6dOzVp0iSfbQcOHNCOHTtUUlKiYcOGSZIeeeQRTZw4Ub/85S9bLUcAAOCbJaDv2WlubtbMmTO1dOlSDRgwoMX2oqIiRUdHe4uOJKWmpiooKEjFxcVtztvQ0CCPx+OzAAAAMwV02VmzZo1CQkK0ePHiVre73W7FxcX5jIWEhCgmJkZut7vNeXNychQVFeVdEhMT/ZobAAAEjoAtO6Wlpfr1r3+tp556Sg6Hw69zZ2VlqaamxrtUVFT4dX4AABA4ArbsvPnmm6qqqlJSUpJCQkIUEhKio0eP6mc/+5n69OkjSXI6naqqqvI57uzZszpx4oScTmebc4eFhSkyMtJnAQAAZrL1BuVzmTlzplJTU33Gxo8fr5kzZ2r27NmSpJSUFFVXV6u0tFTXXnutJGnXrl1qbm7W8OHDOz0zAAAIPLaWndraWh0+fNi7fuTIEZWXlysmJkZJSUmKjY312b9bt25yOp268sorJUn9+/fXjTfeqHnz5ikvL0+NjY1auHChZsyYwTuxAACAJJsvY+3fv19Dhw7V0KFDJUmZmZkaOnSoVqxY8ZXn2Lx5s/r166exY8dq4sSJGjVqlDZu3NhRkQEAQBdj65md0aNHy7Ksr7z/3/72txZjMTEx2rJlix9TAQAAkwTsDcoAAAD+QNkBAABGo+wAAACjUXYAAIDRKDsAAMBolB0AAGA0yg4AADAaZQcAABiNsgMAAIxG2QEAAEaj7AAAAKNRdgAAgNEoOwAAwGiUHQAAYDTKDgAAMBplBwAAGI2yAwAAjEbZAQAARqPsAAAAo1F2AACA0Sg7AADAaJQdAABgNMoOAAAwGmUHAAAYjbIDAACMRtkBAABGo+wAAACjUXYAAIDRKDsAAMBolB0AAGA0yg4AADAaZQcAABiNsgMAAIxG2QEAAEaj7AAAAKNRdgAAgNEoOwAAwGi2lp09e/Zo8uTJcrlccjgc2rZtm3dbY2Ojli9froEDB6pHjx5yuVz64Q9/qOPHj/vMceLECaWlpSkyMlLR0dGaO3euamtrO/mVAACAQGVr2amrq9PgwYO1YcOGFttOnz6tsrIyZWdnq6ysTC+++KIOHjyo73//+z77paWl6cMPP1R+fr62b9+uPXv2aP78+Z31EgAAQIBzWJZl2R1CkhwOh7Zu3aqpU6e2uU9JSYmuv/56HT16VElJSTpw4ICuuuoqlZSUaNiwYZKkHTt2aOLEifr73/8ul8vV6jwNDQ1qaGjwrns8HiUmJqqmpkaRkZGSpM9zf+e/F9dOPRfcbncEAAAClsfjUVRUlM/P79Z0qXt2ampq5HA4FB0dLUkqKipSdHS0t+hIUmpqqoKCglRcXNzmPDk5OYqKivIuiYmJHR0dAADYpMuUnfr6ei1fvly33Xabt7253W7FxcX57BcSEqKYmBi53e4258rKylJNTY13qaio6NDsAADAPiF2B/gqGhsbdcstt8iyLOXm5l7wfGFhYQoLC/NDMgAAEOgCvux8WXSOHj2qXbt2+VyTczqdqqqq8tn/7NmzOnHihJxOZ2dHBQAAASigL2N9WXQOHTqk119/XbGxsT7bU1JSVF1drdLSUu/Yrl271NzcrOHDh3d2XAAAEIBsPbNTW1urw4cPe9ePHDmi8vJyxcTEKCEhQTfffLPKysq0fft2NTU1ee/DiYmJUWhoqPr3768bb7xR8+bNU15enhobG7Vw4ULNmDGjzXdiAQCAbxZby87+/fv13e9+17uemZkpSZo1a5buuecevfzyy5KkIUOG+By3e/dujR49WpK0efNmLVy4UGPHjlVQUJCmTZum9evXd0p+AAAQ+GwtO6NHj9a5HvPzVR4BFBMToy1btvgzFgAAMEhA37MDAABwoSg7AADAaJQdAABgNMoOAAAwGmUHAAAYjbIDAACMRtkBAABGo+wAAACjUXYAAIDRKDsAAMBolB0AAGA0yg4AADAaZQcAABiNsgMAAIxG2QEAAEaj7AAAAKNRdgAAgNEoOwAAwGiUHQAAYDTKDgAAMBplBwAAGI2yAwAAjEbZAQAARqPsAAAAo1F2AACA0Sg7AADAaCF2BwAAAIGv8tdFdkeQJMUvSfnax3BmBwAAGI2yAwAAjEbZAQAARqPsAAAAo1F2AACA0Sg7AADAaJQdAABgNMoOAAAwGg8VBOA3k7b+wu4IkqQ//WCp3REABBBbz+zs2bNHkydPlsvlksPh0LZt23y2W5alFStWKCEhQeHh4UpNTdWhQ4d89jlx4oTS0tIUGRmp6OhozZ07V7W1tZ34KgAAQCCztezU1dVp8ODB2rBhQ6vb165dq/Xr1ysvL0/FxcXq0aOHxo8fr/r6eu8+aWlp+vDDD5Wfn6/t27drz549mj9/fme9BAAAEOBsvYw1YcIETZgwodVtlmVp3bp1uvvuuzVlyhRJ0tNPP634+Hht27ZNM2bM0IEDB7Rjxw6VlJRo2LBhkqRHHnlEEydO1C9/+Uu5XK5Oey0AACAwBewNykeOHJHb7VZqaqp3LCoqSsOHD1dR0T8+jKyoqEjR0dHeoiNJqampCgoKUnFxcZtzNzQ0yOPx+CwAAMBMAVt23G63JCk+Pt5nPD4+3rvN7XYrLi7OZ3tISIhiYmK8+7QmJydHUVFR3iUxMdHP6QEAQKAI2LLTkbKyslRTU+NdKioq7I4EAAA6SMCWHafTKUmqrKz0Ga+srPRuczqdqqqq8tl+9uxZnThxwrtPa8LCwhQZGemzAAAAMwVs2UlOTpbT6VRBQYF3zOPxqLi4WCkpKZKklJQUVVdXq7S01LvPrl271NzcrOHDh3d6ZgAAEHhsfTdWbW2tDh8+7F0/cuSIysvLFRMTo6SkJGVkZGj16tXq27evkpOTlZ2dLZfLpalTp0qS+vfvrxtvvFHz5s1TXl6eGhsbtXDhQs2YMYN3YgEAAEk2l539+/fru9/9rnc9MzNTkjRr1iw99dRTWrZsmerq6jR//nxVV1dr1KhR2rFjh7p37+49ZvPmzVq4cKHGjh2roKAgTZs2TevXr+/01wIAAAKTrWVn9OjRsiyrze0Oh0OrVq3SqlWr2twnJiZGW7Zs6Yh4AADAAAF7zw4AAIA/UHYAAIDRKDsAAMBolB0AAGA0yg4AADAaZQcAABiNsgMAAIxm63N2AADoaK/+4f/ZHUETbr3E7gjfaJzZAQAARqPsAAAAo1F2AACA0Sg7AADAaJQdAABgNMoOAAAwGm89BwDAZn9b57Y7gvpkOO2O0GE4swMAAIxG2QEAAEaj7AAAAKNRdgAAgNG4QRkA0C6Lt1bYHUGStP4HiXZHQIDjzA4AADAaZQcAABiNsgMAAIxG2QEAAEaj7AAAAKNRdgAAgNF46zkg6bFnxtsdQT+ZudPuCABgJM7sAAAAo1F2AACA0dpVdsaMGaPq6uoW4x6PR2PGjLnQTAAAAH7TrrLzxhtv6MyZMy3G6+vr9eabb15wKAAAAH/5Wjco/+///q/3zx999JHcbrd3vampSTt27NCll17qv3QAAAAX6GuVnSFDhsjhcMjhcLR6uSo8PFyPPPKI38IBAABcqK9Vdo4cOSLLsnTZZZdp37596tmzp3dbaGio4uLiFBwc7PeQAAAA7fW1yk7v3r0lSc3NzR0SBgAAwN/a/VDBQ4cOaffu3aqqqmpRflasWHHBwQAAAPyhXWXn8ccf14IFC3TJJZfI6XTK4XB4tzkcDsoOAFygqc8X2B1B224ea3cEwC/a9dbz1atX6/7775fb7VZ5ebneffdd71JWVua3cE1NTcrOzlZycrLCw8N1+eWX67777pNlWd59LMvSihUrlJCQoPDwcKWmpurQoUN+ywAAALq2dpWdkydPavr06f7O0sKaNWuUm5ur3/zmNzpw4IDWrFmjtWvX+rzja+3atVq/fr3y8vJUXFysHj16aPz48aqvr+/wfAAAIPC1q+xMnz5dr732mr+ztPDOO+9oypQpmjRpkvr06aObb75Z48aN0759+yT946zOunXrdPfdd2vKlCkaNGiQnn76aR0/flzbtm1rc96GhgZ5PB6fBQAAmKld9+xcccUVys7O1t69ezVw4EB169bNZ/vixYv9Em7EiBHauHGjPv74Y33729/We++9p7feeksPP/ywpH+8Fd7tdis1NdV7TFRUlIYPH66ioiLNmDGj1XlzcnJ07733+iUjAAAIbO0qOxs3btRFF12kwsJCFRYW+mxzOBx+Kzt33XWXPB6P+vXrp+DgYDU1Nen+++9XWlqaJHmf4BwfH+9zXHx8vM/Tnf9dVlaWMjMzvesej0eJiYl+yQwAAAJLu8rOkSNH/J2jVc8995w2b96sLVu2aMCAASovL1dGRoZcLpdmzZrV7nnDwsIUFhbmx6QAACBQtfs5O51h6dKluuuuu7yXowYOHKijR48qJydHs2bNktPplCRVVlYqISHBe1xlZaWGDBliR2QAXcD3nt9sdwRtvznN7gjAN0a7ys6cOXPOuf3JJ59sV5h/d/r0aQUF+d5DHRwc7H2IYXJyspxOpwoKCrzlxuPxqLi4WAsWLPBLBgAA0LW1q+ycPHnSZ72xsVEffPCBqqurW/2A0PaaPHmy7r//fiUlJWnAgAF699139fDDD3vLlsPhUEZGhlavXq2+ffsqOTlZ2dnZcrlcmjp1qt9yAACArqtdZWfr1q0txpqbm7VgwQJdfvnlFxzqS4888oiys7N1xx13qKqqSi6XSz/5yU98ntC8bNky1dXVaf78+aqurtaoUaO0Y8cOde/e3W85AABA1+W3e3aCgoKUmZmp0aNHa9myZX6ZMyIiQuvWrdO6deva3MfhcGjVqlVatWqVX/5OAABglnY9VLAtn3zyic6ePevPKQEAAC5Iu87s/OszaqR/PMn4s88+05/+9KcLeks4AACAv7Wr7Lz77rs+60FBQerZs6ceeuih875TCwAAoDO1q+zs3r3b3zkAAAA6xAXdoPz555/r4MGDkqQrr7xSPXv29EsoAAAAf2nXDcp1dXWaM2eOEhISdMMNN+iGG26Qy+XS3Llzdfr0aX9nBAAAaLd2lZ3MzEwVFhbqlVdeUXV1taqrq/XSSy+psLBQP/vZz/ydEQAAoN3adRnrhRde0PPPP6/Ro0d7xyZOnKjw8HDdcsstys3N9Vc+AACAC9KuMzunT59WfHx8i/G4uDguYwEAgIDSrrKTkpKilStXqr6+3jv2xRdf6N5771VKSorfwgEAAFyodl3GWrdunW688Ub16tVLgwcPliS99957CgsL02uvvebXgAAAABeiXWVn4MCBOnTokDZv3qy//OUvkqTbbrtNaWlpCg8P92tAdG07n5hodwRJ0vi5f7Y7AgDAJu0qOzk5OYqPj9e8efN8xp988kl9/vnnWr58uV/CAQAAXKh23bPz2GOPqV+/fi3GBwwYoLy8vAsOBQAA4C/tKjtut1sJCQktxnv27KnPPvvsgkMBAAD4S7vKTmJiot5+++0W42+//bZcLtcFhwIAAPCXdt2zM2/ePGVkZKixsVFjxoyRJBUUFGjZsmU8QRkAAASUdpWdpUuX6v/+7/90xx136MyZM5Kk7t27a/ny5crKyvJrQAAAgAvRrrLjcDi0Zs0aZWdn68CBAwoPD1ffvn0VFhbm73wAAAAXpF1l50sXXXSRrrvuOn9lAQAA8Lt23aAMAADQVVzQmR0AnWf21hvtjqBNP9hhdwQA+No4swMAAIxG2QEAAEaj7AAAAKNRdgAAgNEoOwAAwGiUHQAAYDTKDgAAMBplBwAAGI2yAwAAjEbZAQAARqPsAAAAo1F2AACA0Sg7AADAaJQdAABgtIAvO8eOHdPtt9+u2NhYhYeHa+DAgdq/f793u2VZWrFihRISEhQeHq7U1FQdOnTIxsQAACCQBHTZOXnypEaOHKlu3brp1Vdf1UcffaSHHnpIF198sXeftWvXav369crLy1NxcbF69Oih8ePHq76+3sbkAAAgUITYHeBc1qxZo8TERG3atMk7lpyc7P2zZVlat26d7r77bk2ZMkWS9PTTTys+Pl7btm3TjBkzOj0zAAAILAF9Zufll1/WsGHDNH36dMXFxWno0KF6/PHHvduPHDkit9ut1NRU71hUVJSGDx+uoqKiNudtaGiQx+PxWQAAgJkCuuz89a9/VW5urvr27audO3dqwYIFWrx4sX77299KktxutyQpPj7e57j4+Hjvttbk5OQoKirKuyQmJnbciwAAALYK6LLT3Nysa665Rg888ICGDh2q+fPna968ecrLy7ugebOyslRTU+NdKioq/JQYAAAEmoC+ZychIUFXXXWVz1j//v31wgsvSJKcTqckqbKyUgkJCd59KisrNWTIkDbnDQsLU1hYmP8Dd7JP199sdwQlLX7e7ggAAJxTQJ/ZGTlypA4ePOgz9vHHH6t3796S/nGzstPpVEFBgXe7x+NRcXGxUlJSOjUrAAAITAF9ZufOO+/UiBEj9MADD+iWW27Rvn37tHHjRm3cuFGS5HA4lJGRodWrV6tv375KTk5Wdna2XC6Xpk6dam94AAAQEAK67Fx33XXaunWrsrKytGrVKiUnJ2vdunVKS0vz7rNs2TLV1dVp/vz5qq6u1qhRo7Rjxw51797dxuQAACBQBHTZkaTvfe97+t73vtfmdofDoVWrVmnVqlWdmAoAAHQVAX3PDgAAwIWi7AAAAKNRdgAAgNEoOwAAwGiUHQAAYDTKDgAAMBplBwAAGI2yAwAAjEbZAQAARqPsAAAAo1F2AACA0Sg7AADAaJQdAABgNMoOAAAwGmUHAAAYjbIDAACMRtkBAABGo+wAAACjUXYAAIDRKDsAAMBolB0AAGA0yg4AADAaZQcAABiNsgMAAIxG2QEAAEaj7AAAAKNRdgAAgNEoOwAAwGiUHQAAYDTKDgAAMBplBwAAGI2yAwAAjEbZAQAARqPsAAAAo1F2AACA0Sg7AADAaJQdAABgtC5Vdh588EE5HA5lZGR4x+rr65Wenq7Y2FhddNFFmjZtmiorK+0LCQAAAkqXKTslJSV67LHHNGjQIJ/xO++8U6+88or++Mc/qrCwUMePH9dNN91kU0oAABBoukTZqa2tVVpamh5//HFdfPHF3vGamho98cQTevjhhzVmzBhde+212rRpk9555x3t3bvXxsQAACBQdImyk56erkmTJik1NdVnvLS0VI2NjT7j/fr1U1JSkoqKitqcr6GhQR6Px2cBAABmCrE7wPk8++yzKisrU0lJSYttbrdboaGhio6O9hmPj4+X2+1uc86cnBzde++9/o4KAAACUECf2amoqNCSJUu0efNmde/e3W/zZmVlqaamxrtUVFT4bW4AABBYArrslJaWqqqqStdcc41CQkIUEhKiwsJCrV+/XiEhIYqPj9eZM2dUXV3tc1xlZaWcTmeb84aFhSkyMtJnAQAAZgroy1hjx47V+++/7zM2e/Zs9evXT8uXL1diYqK6deumgoICTZs2TZJ08OBBffrpp0pJSbEjMgAACDABXXYiIiJ09dVX+4z16NFDsbGx3vG5c+cqMzNTMTExioyM1KJFi5SSkqLvfOc7dkQGAAABJqDLzlfxq1/9SkFBQZo2bZoaGho0fvx4Pfroo3bHAgAAAaLLlZ033njDZ7179+7asGGDNmzYYE8gAAAQ0AL6BmUAAIALRdkBAABGo+wAAACjUXYAAIDRKDsAAMBolB0AAGA0yg4AADAaZQcAABiNsgMAAIxG2QEAAEaj7AAAAKNRdgAAgNEoOwAAwGiUHQAAYDTKDgAAMBplBwAAGI2yAwAAjEbZAQAARqPsAAAAo1F2AACA0Sg7AADAaJQdAABgNMoOAAAwGmUHAAAYjbIDAACMRtkBAABGo+wAAACjUXYAAIDRKDsAAMBolB0AAGA0yg4AADAaZQcAABiNsgMAAIxG2QEAAEaj7AAAAKNRdgAAgNEoOwAAwGgBXXZycnJ03XXXKSIiQnFxcZo6daoOHjzos099fb3S09MVGxuriy66SNOmTVNlZaVNiQEAQKAJ6LJTWFio9PR07d27V/n5+WpsbNS4ceNUV1fn3efOO+/UK6+8oj/+8Y8qLCzU8ePHddNNN9mYGgAABJIQuwOcy44dO3zWn3rqKcXFxam0tFQ33HCDampq9MQTT2jLli0aM2aMJGnTpk3q37+/9u7dq+985zutztvQ0KCGhgbvusfj6bgXAQAAbBXQZ3b+XU1NjSQpJiZGklRaWqrGxkalpqZ69+nXr5+SkpJUVFTU5jw5OTmKioryLomJiR0bHAAA2KbLlJ3m5mZlZGRo5MiRuvrqqyVJbrdboaGhio6O9tk3Pj5ebre7zbmysrJUU1PjXSoqKjoyOgAAsFFAX8b6V+np6frggw/01ltvXfBcYWFhCgsL80MqAAAQ6LrEmZ2FCxdq+/bt2r17t3r16uUddzqdOnPmjKqrq332r6yslNPp7OSUAAAgEAV02bEsSwsXLtTWrVu1a9cuJScn+2y/9tpr1a1bNxUUFHjHDh48qE8//VQpKSmdHRcAAASggL6MlZ6eri1btuill15SRESE9z6cqKgohYeHKyoqSnPnzlVmZqZiYmIUGRmpRYsWKSUlpc13YgEAgG+WgC47ubm5kqTRo0f7jG/atEk/+tGPJEm/+tWvFBQUpGnTpqmhoUHjx4/Xo48+2slJAQBAoArosmNZ1nn36d69uzZs2KANGzZ0QiIAANDVBPQ9OwAAABeKsgMAAIxG2QEAAEaj7AAAAKNRdgAAgNEoOwAAwGiUHQAAYDTKDgAAMBplBwAAGI2yAwAAjEbZAQAARqPsAAAAo1F2AACA0Sg7AADAaJQdAABgNMoOAAAwGmUHAAAYjbIDAACMRtkBAABGo+wAAACjUXYAAIDRKDsAAMBolB0AAGA0yg4AADAaZQcAABiNsgMAAIxG2QEAAEaj7AAAAKNRdgAAgNEoOwAAwGiUHQAAYDTKDgAAMBplBwAAGI2yAwAAjEbZAQAARqPsAAAAoxlTdjZs2KA+ffqoe/fuGj58uPbt22d3JAAAEACMKDt/+MMflJmZqZUrV6qsrEyDBw/W+PHjVVVVZXc0AABgMyPKzsMPP6x58+Zp9uzZuuqqq5SXl6dvfetbevLJJ+2OBgAAbBZid4ALdebMGZWWliorK8s7FhQUpNTUVBUVFbV6TENDgxoaGrzrNTU1kiSPx+MdO/XFFx2U+KsL+5c8rTlV39hJSdrmOU/Gui/szyidP+cXX5ztpCRtO1/GM6cDP2Pj6fpOSnJu5895upOStO38Ges6KUnbzv9v8lQnJTm38+U8HQA5PZ7Qc24/VR8IGb91zu2n6u3/NylJ4f/y3/vL//aWZZ37IKuLO3bsmCXJeuedd3zGly5dal1//fWtHrNy5UpLEgsLCwsLC4sBS0VFxTm7Qpc/s9MeWVlZyszM9K43NzfrxIkTio2NlcPhuOD5PR6PEhMTVVFRocjIyAuer6N0hZxk9J+ukJOM/tMVcpLRf7pCzo7IaFmWTp06JZfLdc79unzZueSSSxQcHKzKykqf8crKSjmdzlaPCQsLU1hYmM9YdHS037NFRkYG7D+6f9UVcpLRf7pCTjL6T1fISUb/6Qo5/Z0xKirqvPt0+RuUQ0NDde2116qgoMA71tzcrIKCAqWkpNiYDAAABIIuf2ZHkjIzMzVr1iwNGzZM119/vdatW6e6ujrNnj3b7mgAAMBmRpSdW2+9VZ9//rlWrFght9utIUOGaMeOHYqPj7clT1hYmFauXNniUlmg6Qo5yeg/XSEnGf2nK+Qko/90hZx2ZnRY1vnerwUAANB1dfl7dgAAAM6FsgMAAIxG2QEAAEaj7AAAAKNRdvxoz549mjx5slwulxwOh7Zt22Z3pBZycnJ03XXXKSIiQnFxcZo6daoOHjxod6wWcnNzNWjQIO/Dp1JSUvTqq6/aHeucHnzwQTkcDmVkZNgdxeuee+6Rw+HwWfr162d3rFYdO3ZMt99+u2JjYxUeHq6BAwdq//79dsfy6tOnT4uvpcPhUHp6ut3RvJqampSdna3k5GSFh4fr8ssv13333Xf+zw3qZKdOnVJGRoZ69+6t8PBwjRgxQiUlJbZmOt/3b8uytGLFCiUkJCg8PFypqak6dOhQQGV88cUXNW7cOO+nAZSXl3dqvq+Ss7GxUcuXL9fAgQPVo0cPuVwu/fCHP9Tx48c7NBNlx4/q6uo0ePBgbdiwwe4obSosLFR6err27t2r/Px8NTY2aty4caqrC4wPePtSr1699OCDD6q0tFT79+/XmDFjNGXKFH344Yd2R2tVSUmJHnvsMQ0aNMjuKC0MGDBAn332mXd566237I7UwsmTJzVy5Eh169ZNr776qj766CM99NBDuvjii+2O5lVSUuLzdczPz5ckTZ8+3eZk/7RmzRrl5ubqN7/5jQ4cOKA1a9Zo7dq1euSRR+yO5uPHP/6x8vPz9cwzz+j999/XuHHjlJqaqmPHjtmW6Xzfv9euXav169crLy9PxcXF6tGjh8aPH6/6+s778NvzZayrq9OoUaO0Zs2aTsvUVo62cp4+fVplZWXKzs5WWVmZXnzxRR08eFDf//73OzaUPz6MEy1JsrZu3Wp3jPOqqqqyJFmFhYV2Rzmviy++2Pqf//kfu2O0cOrUKatv375Wfn6+9Z//+Z/WkiVL7I7ktXLlSmvw4MF2xziv5cuXW6NGjbI7xteyZMkS6/LLL7eam5vtjuI1adIka86cOT5jN910k5WWlmZTopZOnz5tBQcHW9u3b/cZv+aaa6yf//znNqXy9e/fv5ubmy2n02n94he/8I5VV1dbYWFh1u9//3sbEp77Z8yRI0csSda7777bqZla81V+Fu7bt8+SZB09erTDcnBm5xuupqZGkhQTE2NzkrY1NTXp2WefVV1dXUB+BEh6eromTZqk1NRUu6O06tChQ3K5XLrsssuUlpamTz/91O5ILbz88ssaNmyYpk+frri4OA0dOlSPP/643bHadObMGf3ud7/TnDlz/PLhwf4yYsQIFRQU6OOPP5Ykvffee3rrrbc0YcIEm5P909mzZ9XU1KTu3bv7jIeHhwfkWUdJOnLkiNxut8//41FRURo+fLiKiopsTGaGmpoaORyODvmMyi8Z8QRltE9zc7MyMjI0cuRIXX311XbHaeH9999XSkqK6uvrddFFF2nr1q266qqr7I7l49lnn1VZWZnt9xu0Zfjw4Xrqqad05ZVX6rPPPtO9996r//iP/9AHH3ygiIgIu+N5/fWvf1Vubq4yMzP13//93yopKdHixYsVGhqqWbNm2R2vhW3btqm6ulo/+tGP7I7i46677pLH41G/fv0UHByspqYm3X///UpLS7M7mldERIRSUlJ03333qX///oqPj9fvf/97FRUV6YorrrA7XqvcbrcktXgqf3x8vHcb2qe+vl7Lly/Xbbfd1qEfYErZ+QZLT0/XBx98ELC/TV155ZUqLy9XTU2Nnn/+ec2aNUuFhYUBU3gqKiq0ZMkS5efnt/gtNVD862/0gwYN0vDhw9W7d28999xzmjt3ro3JfDU3N2vYsGF64IEHJElDhw7VBx98oLy8vIAsO0888YQmTJggl8tldxQfzz33nDZv3qwtW7ZowIABKi8vV0ZGhlwuV0B9HZ955hnNmTNHl156qYKDg3XNNdfotttuU2lpqd3R0IkaGxt1yy23yLIs5ebmdujfxWWsb6iFCxdq+/bt2r17t3r16mV3nFaFhobqiiuu0LXXXqucnBwNHjxYv/71r+2O5VVaWqqqqipdc801CgkJUUhIiAoLC7V+/XqFhISoqanJ7ogtREdH69vf/rYOHz5sdxQfCQkJLUps//79A/KS29GjR/X666/rxz/+sd1RWli6dKnuuusuzZgxQwMHDtTMmTN15513Kicnx+5oPi6//HIVFhaqtrZWFRUV2rdvnxobG3XZZZfZHa1VTqdTklRZWekzXllZ6d2Gr+fLonP06FHl5+d36FkdibLzjWNZlhYuXKitW7dq165dSk5OtjvSV9bc3KyGhga7Y3iNHTtW77//vsrLy73LsGHDlJaWpvLycgUHB9sdsYXa2lp98sknSkhIsDuKj5EjR7Z4BMLHH3+s3r1725SobZs2bVJcXJwmTZpkd5QWTp8+raAg32/rwcHBam5utinRufXo0UMJCQk6efKkdu7cqSlTptgdqVXJyclyOp0qKCjwjnk8HhUXFwfkfYSB7suic+jQIb3++uuKjY3t8L+Ty1h+VFtb6/Mb85EjR1ReXq6YmBglJSXZmOyf0tPTtWXLFr300kuKiIjwXm+OiopSeHi4zen+KSsrSxMmTFBSUpJOnTqlLVu26I033tDOnTvtjuYVERHR4l6nHj16KDY2NmDugfqv//ovTZ48Wb1799bx48e1cuVKBQcH67bbbrM7mo8777xTI0aM0AMPPKBbbrlF+/bt08aNG7Vx40a7o/lobm7Wpk2bNGvWLIWEBN63z8mTJ+v+++9XUlKSBgwYoHfffVcPP/yw5syZY3c0Hzt37pRlWbryyit1+PBhLV26VP369dPs2bNty3S+798ZGRlavXq1+vbtq+TkZGVnZ8vlcmnq1KkBk/HEiRP69NNPvc+s+fIXCKfT2alnoM6VMyEhQTfffLPKysq0fft2NTU1eX8OxcTEKDQ0tGNCddj7vL6Bdu/ebUlqscyaNcvuaF6t5ZNkbdq0ye5oPubMmWP17t3bCg0NtXr27GmNHTvWeu211+yOdV6B9tbzW2+91UpISLBCQ0OtSy+91Lr11lutw4cP2x2rVa+88op19dVXW2FhYVa/fv2sjRs32h2phZ07d1qSrIMHD9odpVUej8dasmSJlZSUZHXv3t267LLLrJ///OdWQ0OD3dF8/OEPf7Auu+wyKzQ01HI6nVZ6erpVXV1ta6bzff9ubm62srOzrfj4eCssLMwaO3Zsp/87OF/GTZs2tbp95cqVAZPzy7fFt7bs3r27wzI5LCvAHq0JAADgR9yzAwAAjEbZAQAARqPsAAAAo1F2AACA0Sg7AADAaJQdAABgNMoOAAAwGmUHAAAYjbIDAK245557NGTIELtjAPADyg6AbzyHw6Ft27bZHQNAB6HsAAAAo1F2AASM0aNHa9GiRcrIyNDFF1+s+Ph4Pf7446qrq9Ps2bMVERGhK664Qq+++qr3mMLCQl1//fUKCwtTQkKC7rrrLp09e9ZnzsWLF2vZsmWKiYmR0+nUPffc493ep08fSdIPfvADORwO7/qXnnnmGfXp00dRUVGaMWOGTp061ZFfAgAdgLIDIKD89re/1SWXXKJ9+/Zp0aJFWrBggaZPn64RI0aorKxM48aN08yZM3X69GkdO3ZMEydO1HXXXaf33ntPubm5euKJJ7R69eoWc/bo0UPFxcVau3atVq1apfz8fElSSUmJJGnTpk367LPPvOuS9Mknn2jbtm3avn27tm/frsLCQj344IOd98UA4Bd86jmAgDF69Gg1NTXpzTfflCQ1NTUpKipKN910k55++mlJktvtVkJCgoqKivTKK6/ohRde0IEDB+RwOCRJjz76qJYvX66amhoFBQW1mFOSrr/+eo0ZM8ZbXBwOh7Zu3aqpU6d697nnnnv0i1/8Qm63WxEREZKkZcuWac+ePdq7d29nfDkA+AlndgAElEGDBnn/HBwcrNjYWA0cONA7Fh8fL0mqqqrSgQMHlJKS4i06kjRy5EjV1tbq73//e6tzSlJCQoKqqqrOm6VPnz7eovN1jgMQWCg7AAJKt27dfNYdDofP2JfFprm5+YLm/CrHt/c4AIGFsgOgy+rfv7+Kior0r1fj3377bUVERKhXr15feZ5u3bqpqampIyICCACUHQBd1h133KGKigotWrRIf/nLX/TSSy9p5cqVyszMVFDQV//21qdPHxUUFMjtduvkyZMdmBiAHSg7ALqsSy+9VH/+85+1b98+DR48WD/96U81d+5c3X333V9rnoceekj5+flKTEzU0KFDOygtALvwbiwAAGA0zuwAAACjUXYAAIDRKDsAAMBolB0AAGA0yg4AADAaZQcAABiNsgMAAIxG2QEAAEaj7AAAAKNRdgAAgNEoOwAAwGj/H/T2d+e5Q35vAAAAAElFTkSuQmCC\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "sns.countplot(x=\"director\", hue=\"rating\",data=clean_columns_mov_info)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 467
        },
        "id": "1ucSZaOgXH0l",
        "outputId": "a54b3bf8-1e96-47cc-9cc3-b7d68672bacb"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "<Axes: xlabel='director', ylabel='count'>"
            ]
          },
          "metadata": {},
          "execution_count": 72
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "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MY0cOVIHDx5UjRo11K5dO23evLnYC2oAAAAAKJrNcPtyuEBGRoaCg4OVnp6uoKAgd5cDAKjEsrOzlZqaqoYNG8rX19fd5VR5Ja1vfr+B8sU5WwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAW83F0AAABAca586coKm9em+zaVeZzhw4dr8eLFkiRvb2/Vr19fw4YN08SJE+Xl5SVjjF5//XUtWLBAO3fuVH5+vqKiotSzZ0/dd999io6OLnban3/+uWbMmKGtW7cqLS1Ny5Yt04ABA5z6TJkyRUuXLtWBAwfk4+Ojdu3aadq0abr88svLvCwAyh97tgAAAC5Ar169lJaWpj179ujBBx/UlClTNGPGDBljNGTIEN1///3q06ePPvvsM/3444+aP3++fH199eSTT5Y43aysLLVq1UqzZ88utk9sbKxefvllbd++XV988YUaNGiga665RkeOHCnvxQRwHtizBQAAcAHsdrvCw8MlSXfffbeWLVumjz76SA0bNtTSpUu1YsUK9e/f3+pfv359XXHFFTLGlDjd3r17q3fv3iX2GTJkiNPj559/XvPnz9cPP/ygHj16nOcSASgv7NkCAAAoR35+fsrNzdW//vUvxcXFOQWtgmw2W7nONzc3V/PmzVNwcLBatWpVrtMGcH4IWwAAAOXAGKM1a9Zo1apV6t69u37++WfFxcU59RkzZowCAwMVGBioevXqlct8V65cqcDAQPn6+mrmzJlavXq1ateuXS7TBnBhCFsAAAAXoGDY6d27twYNGqQpU6YU2feRRx5RSkqKJk2apMzMTEnSxo0brQAWGBiot99+u0zz79atm1JSUrR582b16tVLN954ow4fPnyhiwWgHHDOFgAAwAXo1q2b5syZIx8fH9WtW1deXmc2r2JiYrR7926nviEhIQoJCVFoaKg1rH379kpJSbEeh4WFlWn+AQEBio6OVnR0tK644grFxMRo/vz5mjBhwvkvFIBywZ4tAACAC+AIO/Xr17eCliQNHjxYu3fv1ooVK0oc38/PzwpL0dHRqlat2gXVk5+fr5ycnAuaBoDywZ4tAAAAF7jpppv04Ycf6qabbtKECROUkJCgsLAw7du3T++88448PT1LHD8zM1N79+61HqempiolJUU1a9ZU/fr1lZWVpWnTpql///6qU6eO/vrrL82ePVt//PGHBg4c6OrFA1AK7NkCAABwAZvNpnfeeUezZs3Sp59+qh49eiguLk4jRoxQZGSkvvjiixLH//bbb9WmTRu1adNGkjR27Fi1adNGkyZNkiR5enrqp59+0g033KDY2Fj169dPR48e1caNG9WsWTOXLx+Ac7OZc93kATgPGRkZCg4OVnp6uoKCgtxdDgCgEsvOzlZqaqoaNmwoX19fd5dT5ZW0vvn9BsoXe7YAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIWwAAAADgAl7uLgAAAKA4Gzp3qbB5dfl8Q5nHGT58uBYvXqzk5GQ9/PDD1vDly5fruuuukzFG69evV7du3aznateurQ4dOmj69Olq0aJFudQOoHJizxYAAMAF8PX11fTp03Xs2LES++3evVtpaWlatWqVcnJy1LdvX+Xm5lZQlQDcgbAFAABwAXr27Knw8HAlJyeX2C80NFTh4eFq27atxowZowMHDuinn36qoCoBuANhCwAA4AJ4enrqqaee0ksvvaTff//9nP3T09O1dOlSSZKPj4+rywPgRoStKm7OnDlq2bKlgoKCFBQUpPj4eP3f//1fieO89957uuyyy+Tr66sWLVro008/raBqAQC4OF133XVq3bq1Jk+eXGyfevXqKTAwUNWrV9eSJUvUv39/XXbZZRVYJYCKRtiq4urVq6enn35aW7du1bfffqvu3bsrMTFRO3fuLLL/5s2bNXjwYN12223atm2bBgwYoAEDBmjHjh0VXDkAABeX6dOna/Hixdq1a1eRz2/cuFFbt27VokWLFBsbq7lz51ZwhQAqGmGriuvXr5/69OmjmJgYxcbGatq0aQoMDNSXX35ZZP8XXnhBvXr10rhx49SkSRM98cQTatu2rV5++eUKrhwAgItL586dlZCQoAkTJhT5fMOGDRUXF6ekpCTdfvvtGjRoUAVXCKCiEbYuIXl5eVq6dKmysrIUHx9fZJ8tW7aoZ8+eTsMSEhK0ZcuWEqedk5OjjIwMpwYAwKXm6aef1scff3zO381Ro0Zpx44dWrZsWQVVBsAdCFuXgO3btyswMFB2u1133XWXli1bpqZNmxbZ9+DBgwoLC3MaFhYWpoMHD5Y4j+TkZAUHB1stMjKy3OoHAOBi0aJFCw0dOlQvvvhiif38/f01cuRITZ48WcaYCqoOQEUjbF0C4uLilJKSoq+++kp33323kpKS9OOPP5brPCZMmKD09HSrHThwoFynDwDAxeLxxx9Xfn7+Ofvde++92rVrl957770KqAqAO3i5uwC4no+Pj6KjoyVJ7dq10zfffKMXXnhBr776aqG+4eHhOnTokNOwQ4cOKTw8vMR52O122e328isaAABJXT7f4O4SSrRo0aJCwxo0aKCcnBzrcdeuXYvcexUZGalTp065sjwAbsaerUtQfn6+049AQfHx8Vq7dq3TsNWrVxd7jhcAAACAorFnq4qbMGGCevfurfr16+vEiRNasmSJ1q9fr1WrVkmShg0bpoiICOuu96NHj1aXLl303HPPqW/fvlq6dKm+/fZbzZs3z52LAQAAAFx0CFtV3OHDhzVs2DClpaUpODhYLVu21KpVq3T11VdLkvbv3y8Pj//t4OzUqZOWLFmiRx99VBMnTlRMTIyWL1+u5s2bu2sRAAAAgIuSzXAJHLhARkaGgoODlZ6erqCgIHeXAwCoxLKzs5WamqqGDRvK19fX3eVUeSWtb36/gfLFOVsAAAAA4AKELQAAAABwAcIWAAAAALgAYQsAAAAAXICwBQAAAAAuQNgCAAAAABfgPlsAAKDSevnBjytsXvc+1++8xjt48KCSk5P1ySef6Pfff1dwcLCio6N18803KykpSf7+/uVcKYCLBWELAADgPP3666+68sorVb16dT311FNq0aKF7Ha7tm/frnnz5ikiIkL9+/d3d5kA3ISwBQAAcJ7uueceeXl56dtvv1VAQIA1vFGjRkpMTJQxxo3VAXA3ztkCAAA4D0ePHtVnn32mUaNGOQWtgmw2WwVXBaAyIWwBAACch71798oYo7i4OKfhtWvXVmBgoAIDA/XQQw+5qToAlQFhCwAAoBx9/fXXSklJUbNmzZSTk+PucgC4EedsAQAAnIfo6GjZbDbt3r3baXijRo0kSX5+fu4oC0Alwp4tAACA81CrVi1dffXVevnll5WVleXucgBUQoQtAACA8/TKK6/o9OnTat++vd555x3t2rVLu3fv1ltvvaWffvpJnp6e7i4RgBtxGCEAAMB5aty4sbZt26annnpKEyZM0O+//y673a6mTZvqn//8p+655x53lwjAjWyGG0DABTIyMhQcHKz09HQFBQW5uxwAQCWWnZ2t1NRUNWzYUL6+vu4up8oraX3z+w2ULw4jBAAAAAAXIGwBAAAAgAsQtgAAAADABQhbAAAAAOAChC0AAAAAcAHCFgAAAAC4AGELAAAAAFyAsAUAAAAALkDYAgAAAAAXIGwBAAAAgAt4ubsAAACA4ky7+R8VNq9H3nq/zOMMHz5cixcvVnJysh5++GFr+PLly3XdddfJGCNJMsbotdde0/z587Vz5055eXkpOjpaN998s+644w75+/tr586dmjRpkrZu3ap9+/Zp5syZGjNmjNP8GjRooH379hWq45577tHs2bPLXD8A12LPFgAAwAXw9fXV9OnTdezYsWL73HLLLRozZowSExO1bt06paSk6LHHHtOKFSv02WefSZJOnjypRo0a6emnn1Z4eHiR0/nmm2+UlpZmtdWrV0uSBg4cWP4LBuCCsWcLAADgAvTs2VN79+5VcnKynnnmmULPv/vuu3r77be1fPlyJSYmWsMbNGig/v37KyMjQ5LUoUMHdejQQZKc9pIVFBIS4vT46aefVuPGjdWlS5fyWhwA5Yg9WwAAABfA09NTTz31lF566SX9/vvvhZ5/++23FRcX5xS0HGw2m4KDg89rvrm5uXrrrbc0YsQI2Wy285oGANcibAEAAFyg6667Tq1bt9bkyZMLPbdnzx7FxcWV+zyXL1+u48ePa/jw4eU+bQDlg7AFAABQDqZPn67Fixdr165dTsMdF8kob/Pnz1fv3r1Vt25dl0wfwIUjbFVxycnJ6tChg6pVq6bQ0FANGDBAu3fvLnGcRYsWyWazOTVfX98KqhgAgItT586dlZCQoAkTJjgNj42N1U8//VSu89q3b5/WrFmj22+/vVynC6B8EbaquA0bNmjUqFH68ssvtXr1ap06dUrXXHONsrKyShwvKCjI6WpHRV1mFgAAOHv66af18ccfa8uWLdawIUOG6Oeff9aKFSsK9TfGKD09vczzWbhwoUJDQ9W3b98LqheAa3E1wiru3//+t9PjRYsWKTQ0VFu3blXnzp2LHc9msxV72VkAAFC0Fi1aaOjQoXrxxRetYTfeeKOWLVumwYMH69FHH9U111yjkJAQbd++XTNnztR9992nAQMGKDc3Vz/++KOkMxe/+OOPP5SSkqLAwEBFR0db08vPz9fChQuVlJQkLy825YDKjD1blxjHX89q1qxZYr/MzExFRUUpMjJSiYmJ2rlzZ4n9c3JylJGR4dQAALgUPf7448rPz7ce22w2LVmyRM8//7yWL1+uLl26qGXLlpoyZYoSExOVkJAgSfrzzz/Vpk0btWnTRmlpaXr22WfVpk2bQocKrlmzRvv379eIESMqdLkAlJ3NuOqsTVQ6+fn56t+/v44fP64vvvii2H5btmzRnj171LJlS6Wnp+vZZ5/V559/rp07d6pevXpFjjNlyhRNnTq10PD09HQFBQWV2zIAAKqe7OxspaamqmHDhpwjXAFKWt8ZGRkKDg7m9xsoJ4StS8jdd9+t//u//9MXX3xRbGgqyqlTp9SkSRMNHjxYTzzxRJF9cnJylJOTYz3OyMhQZGQkX9YAgHMibFUswhZQcTjQ9xJx7733auXKlfr888/LFLQkydvbW23atNHevXuL7WO322W32y+0TAAAAKDK4JytKs4Yo3vvvVfLli3Tf/7zHzVs2LDM08jLy9P27dtVp04dF1QIAAAAVE3s2ariRo0apSVLlmjFihWqVq2aDh48KEkKDg6Wn5+fJGnYsGGKiIhQcnKypDMn9l5xxRWKjo7W8ePHNWPGDO3bt497eQAAAABlQNiq4ubMmSNJ6tq1q9PwhQsXavjw4ZKk/fv3y8Pjfzs5jx07ppEjR+rgwYOqUaOG2rVrp82bN6tp06YVVTYAAABw0eMCGXAJTrAFAJSW44INUVFR8vf3d3c5Vd7Jkye1b98+LpABVAD2bAEAALfy8fGRh4eH/vzzT4WEhMjHx0c2m83dZVU5xhjl5ubqyJEj8vDwkI+Pj7tLAqo8whYAAHArDw8PNWzYUGlpafrzzz/dXU6V5+/vr/r16zudQgDANQhbAADA7Xx8fFS/fn2dPn1aeXl57i6nyvL09JSXlxd7DoEKQtgCAACVgs1mk7e3t7y9vd1dCgCUC/YfAwAAAIALELYAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2KqkunfvruPHjxcanpGRoe7du1d8QQAAAADKhLBVSa1fv165ubmFhmdnZ2vjxo1uqAgAAABAWXi5uwA4++GHH6z///jjjzp48KD1OC8vT//+978VERHhjtIAAAAAlAFhq5Jp3bq1bDabbDZbkYcL+vn56aWXXnJDZQAAAADKgrBVyaSmpsoYo0aNGunrr79WSEiI9ZyPj49CQ0Pl6enpxgoBAAAAlAZhq5KJioqSJOXn57u5EgAAAAAXgrBVie3Zs0fr1q3T4cOHC4WvSZMmuakqAAAAAKVB2KqkXnvtNd19992qXbu2wsPDZbPZrOdsNhthCwAAAKjkCFuV1JNPPqlp06bpoYcecncpAAAAAM4D99mqpI4dO6aBAwe6uwwAAAAA54mwVUkNHDhQn332mbvLAAAAAHCeOIywkoqOjtZjjz2mL7/8Ui1atJC3t7fT8/fff7+bKgMAAABQGjZjjHF3ESisYcOGxT5ns9n066+/VmA1ZZeRkaHg4GClp6crKCjI3eUAAIBS4PcbKF/s2aqkUlNT3V0CAAAAgAvAOVsAAAAA4ALs2aqkRowYUeLzCxYsqKBKAAAAAJwPwlYldezYMafHp06d0o4dO3T8+HF1797dTVUBAAAAKC3CViW1bNmyQsPy8/N19913q3Hjxm6oCAAAAEBZcM7WRcTDw0Njx47VzJkz3V0KAAAAgHMgbF1kfvnlF50+fdrdZQAAAAA4Bw4jrKTGjh3r9NgYo7S0NH3yySdKSkpyU1UAAAAASouwVUlt27bN6bGHh4dCQkL03HPPnfNKhQAAAADcj7BVSa1bt65cppOcnKwPP/xQP/30k/z8/NSpUydNnz5dcXFxJY733nvv6bHHHtNvv/2mmJgYTZ8+XX369CmXmgAAAIBLAedsVXJHjhzRF198oS+++EJHjhwp8/gbNmzQqFGj9OWXX2r16tU6deqUrrnmGmVlZRU7zubNmzV48GDddttt2rZtmwYMGKABAwZox44dF7IoAAAAwCXFZowx7i4ChWVlZem+++7TG2+8ofz8fEmSp6enhg0bppdeekn+/v7nNd0jR44oNDRUGzZsUOfOnYvsM2jQIGVlZWnlypXWsCuuuEKtW7fW3LlzSzWfjIwMBQcHKz09XUFBQedVKwAAqFj8fgPliz1bldTYsWO1YcMGffzxxzp+/LiOHz+uFStWaMOGDXrwwQfPe7rp6emSpJo1axbbZ8uWLerZs6fTsISEBG3ZsqXYcXJycpSRkeHUAAAAgEsZYauS+uCDDzR//nz17t1bQUFBCgoKUp8+ffTaa6/p/fffP69p5ufna8yYMbryyivVvHnzYvsdPHhQYWFhTsPCwsJ08ODBYsdJTk5WcHCw1SIjI8+rRlfY0LmL2+bdbtwbl8Q8z+XKl650dwml5s73CyqX/Y+3cHcJAICLHGGrkjp58mShwCNJoaGhOnny5HlNc9SoUdqxY4eWLl16oeUVMmHCBKWnp1vtwIED5T4PAAAA4GJC2Kqk4uPjNXnyZGVnZ1vD/v77b02dOlXx8fFlnt69996rlStXat26dapXr16JfcPDw3Xo0CGnYYcOHVJ4eHix49jtdmsPnKMBAAAAlzIu/V5JzZo1S7169VK9evXUqlUrSdL3338vu92uzz77rNTTMcbovvvu07Jly7R+/Xo1bNjwnOPEx8dr7dq1GjNmjDVs9erV5xXyAAAAgEsVYauSatGihfbs2aO3335bP/30kyRp8ODBGjp0qPz8/Eo9nVGjRmnJkiVasWKFqlWrZp13FRwcbE1n2LBhioiIUHJysiRp9OjR6tKli5577jn17dtXS5cu1bfffqt58+aV81ICAAAAVRdhq5JKTk5WWFiYRo4c6TR8wYIFOnLkiB566KFSTWfOnDmSpK5duzoNX7hwoYYPHy5J2r9/vzw8/ndEaadOnbRkyRI9+uijmjhxomJiYrR8+fISL6oBAAAAwBlhq5J69dVXtWTJkkLDmzVrpptuuqnUYas0t1Fbv359oWEDBw7UwIEDSzUPAAAAAIVxgYxK6uDBg6pTp06h4SEhIUpLS3NDRQAAAADKgrBVSUVGRmrTpk2Fhm/atEl169Z1Q0UAAAAAyoLDCCupkSNHasyYMTp16pS6d+8uSVq7dq3Gjx+vBx980M3VAQAAADgXwlYlNW7cOB09elT33HOPcnNzJUm+vr566KGHNGHCBDdXBwAAAOBcCFuVlM1m0/Tp0/XYY49p165d8vPzU0xMjOx2u7tLAwAAAFAKhK1KLjAwUB06dHB3GQAAAADKiAtkAAAAAIALELYAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIWwAAAADgAoStKu7zzz9Xv379VLduXdlsNi1fvrzE/uvXr5fNZivUDh48WDEFAwAAAFUEYauKy8rKUqtWrTR79uwyjbd7926lpaVZLTQ01EUVAgAAAFWTl7sLgGv17t1bvXv3LvN4oaGhql69evkXBAAAAFwi2LOFIrVu3Vp16tTR1VdfrU2bNp2zf05OjjIyMpwaAAAAcCkjbMFJnTp1NHfuXH3wwQf64IMPFBkZqa5du+q7774rcbzk5GQFBwdbLTIysoIqBgAAAConDiOEk7i4OMXFxVmPO3XqpF9++UUzZ87Um2++Wex4EyZM0NixY63HGRkZBC4AAABc0ghbOKeOHTvqiy++KLGP3W6X3W6voIoAAACAyo/DCHFOKSkpqlOnjrvLAAAAAC4q7Nmq4jIzM7V3717rcWpqqlJSUlSzZk3Vr19fEyZM0B9//KE33nhDkjRr1iw1bNhQzZo1U3Z2tl5//XX95z//0WeffeauRQAAAAAuSoStKu7bb79Vt27drMeO86qSkpK0aNEipaWlaf/+/dbzubm5evDBB/XHH3/I399fLVu21Jo1a5ymAQAAAODcCFtVXNeuXWWMKfb5RYsWOT0eP368xo8f7+KqAAAAgKqPc7YAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIW1Xc559/rn79+qlu3bqy2Wxavnz5OcdZv3692rZtK7vdrujoaC1atMjldQIAAABVDWGrisvKylKrVq00e/bsUvVPTU1V37591a1bN6WkpGjMmDG6/fbbtWrVKhdXCgAAAFQtXu4uAK7Vu3dv9e7du9T9586dq4YNG+q5556TJDVp0kRffPGFZs6cqYSEBFeVCQAAAFQ57NmCky1btqhnz55OwxISErRly5YSx8vJyVFGRoZTAwAAAC5lhC04OXjwoMLCwpyGhYWFKSMjQ3///Xex4yUnJys4ONhqkZGRxfa98qUr1W7cG4WGFzWsou1/vEWZx9nQuYuufOnKUk/rXMtZ1LSKGlaaaZV2+udrQ+cuRQ4/13p0jFfa+gv2K039xdV1Pu+9lx/8uBQVFj2t4uo4X2VZ9rOXqbTv7Qv5HJb1dSqPeZakLO+zc62fkt4H53pPnV1HwWmV9XUq7vvm7GHl+d4raj2WZfoX8n1QmvVz9rCyrIvz+ZwU994uOG55rp+ilOU12f94iyLfewAqBmEL5WLChAlKT0+32oEDB9xdEgAAAOBWnLMFJ+Hh4Tp06JDTsEOHDikoKEh+fn7Fjme322W3211dHgAAAHDRYM8WnMTHx2vt2rVOw1avXq34+Hg3VQQAAABcnAhbVVxmZqZSUlKUkpIi6cyl3VNSUrR//35JZw7/GzZsmNX/rrvu0q+//qrx48frp59+0iuvvKJ3331XDzzwgDvKBwAAAC5ahK0q7ttvv1WbNm3Upk0bSdLYsWPVpk0bTZo0SZKUlpZmBS9JatiwoT755BOtXr1arVq10nPPPafXX3+dy74DAAAAZcQ5W1Vc165dZYwp9vlFixYVOc62bdtcWBUAAABQ9bFnCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLB1iZg9e7YaNGggX19fXX755fr666+L7bto0SLZbDan5uvrW4HVAgAAABc/wtYl4J133tHYsWM1efJkfffdd2rVqpUSEhJ0+PDhYscJCgpSWlqa1fbt21eBFQMAAAAXP8LWJeD555/XyJEjdeutt6pp06aaO3eu/P39tWDBgmLHsdlsCg8Pt1pYWFgFVgwAAABc/AhbVVxubq62bt2qnj17WsM8PDzUs2dPbdmypdjxMjMzFRUVpcjISCUmJmrnzp0lzicnJ0cZGRlODQAAALiUEbaquL/++kt5eXmF9kyFhYXp4MGDRY4TFxenBQsWaMWKFXrrrbeUn5+vTp066ffffy92PsnJyQoODrZaZGRkuS4HAAAAcLEhbKGQ+Ph4DRs2TK1bt1aXLl304YcfKiQkRK+++mqx40yYMEHp6elWO3DgQAVWDAAAAFQ+Xu4uAK5Vu3ZteXp66tChQ07DDx06pPDw8FJNw9vbW23atNHevXuL7WO322W32y+oVgAAAKAqYc9WFefj46N27dpp7dq11rD8/HytXbtW8fHxpZpGXl6etm/frjp16riqTAAAAKDKYc/WJWDs2LFKSkpS+/bt1bFjR82aNUtZWVm69dZbJUnDhg1TRESEkpOTJUmPP/64rrjiCkVHR+v48eOaMWOG9u3bp9tvv92diwEAAABcVAhbl4BBgwbpyJEjmjRpkg4ePKjWrVvr3//+t3XRjP3798vD4387OY8dO6aRI0fq4MGDqlGjhtq1a6fNmzeradOm7loEAAAA4KJD2LpE3Hvvvbr33nuLfG79+vVOj2fOnKmZM2dWQFUAAABA1cU5WwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIWwAAAADgAoQtAAAAAHABwhYAAAAAuABhCwAAAABcgLAFAAAAAC5A2AIAAAAAFyBsAQAAAIALELYAAAAAwAUIWwAAAADgAoStS8Ts2bPVoEED+fr66vLLL9fXX39dYv/33ntPl112mXx9fdWiRQt9+umnFVQpAAAAUDUQti4B77zzjsaOHavJkyfru+++U6tWrZSQkKDDhw8X2X/z5s0aPHiwbrvtNm3btk0DBgzQgAEDtGPHjgquHAAAALh4EbYuAc8//7xGjhypW2+9VU2bNtXcuXPl7++vBQsWFNn/hRdeUK9evTRu3Dg1adJETzzxhNq2bauXX365gisHAAAALl5e7i4ArpWbm6utW7dqwoQJ1jAPDw/17NlTW7ZsKXKcLVu2aOzYsU7DEhIStHz58mLnk5OTo5ycHOtxenq6JCkjI6NQ39N/n1Zezt+FnitqWHnIOn261NM9kZ1X5hqyTp/W6b8Lz+NEdt55LWdR0ypqWHHTOp/pn6/i1u3Z6/HseTrGK+1rXrBfaeovrq7SvPfOHvfvnJNlWl8lTetClWXZz17O0r63L+RzWNbXqTzmWZKyvM+KWj8Fh5X0Pijte8oxrOC0yvo6Ffd9U9xnrDwUtR7L83u1pNepNOuntN83RTmfz0lx7+2C41bE705pX5OCv0Wl+T5zPG+MKVNNAIpmM3yaqrQ///xTERER2rx5s+Lj463h48eP14YNG/TVV18VGsfHx0eLFy/W4MGDrWGvvPKKpk6dqkOHDhU5nylTpmjq1KnlvwAAAKDCHThwQPXq1XN3GcBFj8MIUS4mTJig9PR0q3F+FwAAF6evv/5adevWdXcZQJXAYYRVXO3ateXp6Vloj9ShQ4cUHh5e5Djh4eFl6i9JdrtddrvdehwcHHwBVQMAAHepU6eOPDz4ezxQHvgkVXE+Pj5q166d1q5daw3Lz8/X2rVrnQ4rLCg+Pt6pvyStXr262P4AAAAACmPP1iVg7NixSkpKUvv27dWxY0fNmjVLWVlZuvXWWyVJw4YNU0REhJKTkyVJo0ePVpcuXfTcc8+pb9++Wrp0qb799lvNmzfPnYsBAAAAXFQIW5eAQYMG6ciRI5o0aZIOHjyo1q1b69///rfCwsIkSfv373c6XKBTp05asmSJHn30UU2cOFExMTFavny5mjdvXup5BgUF6aqrrlK7du301VdfKT8/X9KZKyFefvnlZR52vuNV5nle7NNnmS6O6VfFZWKdXRzzZJkq3/RLM08vLy8FBQUJQPngaoQAAAAA4AKcswUAAAAALkDYAgAAAAAXIGwBAAAAgAsQti5S69evl81m0/Hjx63/BwcH64svvpDNZpPNZrMuejFlyhTVrFlTAwYM0G+//WY9v2/fPkVHR6tOnTqSZA3v0aOHbDabBg0aZA2z2WzauHGjJk2a5DTMZrPp7bff1qxZs2Sz2eTj46MWLVpYzzVv3lwDBgywHj/55JOFxq9fv748PT1ls9nUqlUrazqBgYFO/Xx8fGSz2VS9enVrWEhIiPX/Ro0aFZr2xdAaNGjg9JqV1NexnlzdzlVHUc3b21teXl4VNu/zqdEVzd/fv0Lnd6HruEaNGqXqV9r3Wv369UvVr1q1am5/rRwtICCg3Kfp7e1dqn6+vr4XNJ+SXhdHDXa73Rp2Pu+X0i5LZWiNGzd2enzzzTeXafwL+TyFhITIw8PDaRqO36nzbR4eHoXeIwV/5y50HsuXL1fXrl11zTXXFJp2YGCg4uLiZLPZ5Ofn5zTe9ddf7/R4yJAhGjBggBo0aFDou9jLy/naa473U79+/WSz/e876Pjx41Yfx+9gw4YNi9zmGT58uAYMGKDbb7/dmk9KSor1fNeuXTVmzJhy3c4Cyo1xgy5dupjRo0e7Y9Zm3bp1RpI5duxYuU9r4cKFJjg42BhjTFpamrn//vtN48aNjYeHh5FkJBkPDw8TEhJievbsaebPn29mz55tAgMDzalTp6zpOvrSaDQajUajVdYWERFRaJinp6e1PdO0aVNr+JEjR0xaWpqRZObMmWPy8/Ot56688soip9+hQwcjyQwePNgkJiaasWPHWs998skn1v/Xr19vMjIyrO0yxzRHjx5tkpKSTK1ataztzvz8fDNy5EhTo0YNI8m0a9fO3H///U7DJJlly5YZY4yZPHmySUpKctrGc8ynefPmhbYNa9WqZQICAkrc1k1KSjKJiYlFbk9GRUWZdevWFbvtOXnyZNOqVauSNk/PqeCyGGOclre0zl6Gc3HUXdbtcHdmhvJSprCVlJRkvQm9vLxMgwYNzLhx48zff/9dppmW54pz1HTnnXcWeu6ee+4xkkxSUpJT36Je5LP7OmzevNlIMmFhYebjjz82koyvr6/x8/MzjRo1MpLM559/boz535v3+uuvN3a73Vx22WXmnXfeMYmJiaZz585m4cKFpnv37ub5558306ZNM15eXk5fKjVr1jQJCQnmqaeeMr6+vm7/EqXRaDQajXZptvDw8HP2KWpbxfEH5sDAQKfhnp6eRYazs9unn35qJDlts5XUrrzySrN3716nYZdddplJSUkxt99+uwkICChyvMjISDNhwgRz1VVXmcTEROPt7W02bdpk6tWrZ6Tiw1bBQCfJ1K5d2/Tu3dv88MMPxhhj/Pz8jIeHhzl69KjJyMgoMpQcP37caTu0pLB19rZ3QECACQwMNPPnzzd5eXml2laOiooqtPw2m816vuDyLly48Jzr/IYbbjCRkZEmMTHRpKamWq/777//7jTfP//803h6ehpJZvTo0aZVq1YmJyfHpKWlmfz8/FLVXhXCVpkPI+zVq5fS0tL066+/aubMmXr11Vc1efLksk6mXEVGRmrp0qX6+++/rWHZ2dlasmSJ6tev79Q3JCREkkrVV5Lmz5+vJk2a6PDhw0pMTJQkPfPMM/rhhx8UHx8vSZo9e7bTOF9++aVsNpu+/fZb3Xjjjapevbpq1Kih4cOHa+3atRozZowmTpyo7t27S5K8vLzk5+en7Oxsbdy4UY888ohycnIkSZ6enhe6egAAAMrk4MGD5+yTnZ1daJjjfl6ZmZlOw/Py8vTHH3+cc5p9+vSRJC1evLg0ZWrTpk2Kjo52GvbTTz+pdevWev3115WVlVVoHJvNpj///FPJycnasWOH/v3vf+v06dNKTk7WX3/9JUm66aab1KxZMy1btkzvv/++7rjjDp04cUIbNmywpnPZZZdp1apVysnJUd++fXXy5EnruZo1a6patWpF1hwcHKzq1auXavmk/217//bbbxo6dKgCAwM1evRoXXvttTp9+nSx4+Xm5lr/f/zxx5WWlqa0tDTNmjVLgYGBRY4zaNAgq19aWpri4+M1cuRIp2EBAQGFxouIiNAbb7zhNGzx4sWKiIhwGubj46Pw8HDZbLZC08jLy7PeP6VhjClx+V2pTPMuSzIrKp1ff/31pk2bNtbjv/76y9x0002mbt26xs/PzzRv3twsWbLEaZyzU+rKlStNUFCQeeutt4wxxuzfv98MHDjQBAcHmxo1apj+/fub1NRUY4wxGzZsMF5eXiYtLc2pplq1apnY2FhjjDG//fabadOmjfHw8DCenp4mODjYfPLJJyYpKcnapW23242np6fx8PAwUVFRJjY21iQmJpqbb77ZjBo1yoSHhxtvb28r/avAX2uKa470XlwLDAw0drvdmqZjz5jjsYeHh9M8HPOl0Wg0Go1Go1XuVtxRSTabzcTExJjx48eb2rVrOz0XEBBgHelUvXp1a3hwcLAJDg62tmPff/99079/f+Pv7288PDxMbGyskWSmTZtmGjZsaEaNGmWqV69uQkNDjaenp7HZbCYuLs6cOHHC1KpVywQHBxtJJj4+3jz77LPWYYQffvihkWSWLl1qbYP37dvXeHt7G5vNZmw2m4mMjLS2wydPnlzsslerVs3ceOONpkaNGsbf39/Y7XbTuHFjI53ZRq5WrZq58847jSRTrVo107FjRxMUFGSefvpp4+/vb6T/bZ/bbDYTFhZmPD09jbe3t2nVqpWpVq2akWSGDBli2rZtazw9PU1YWJix2+2mRo0aplq1aqZatWqmW7duJiUlxcoZjkMY33jjDRMVFWWCgoLMoEGDTEZGhtUnLy/PPPXUU6ZBgwbG19fXtGzZ0rz33nvW8469j59++qlp27at8fb2LvFwz4Iu6AIZO3bs0ObNm+Xj42MNy87OVrt27fTJJ59ox44duuOOO3TLLbfo66+/LnIaS5Ys0eDBg/X2229r6NChOnXqlBISElStWjVt3LhRmzZtUmBgoHr16qXc3Fx17txZjRo10ptvvmlNIz8/X9nZ2dZeoFGjRmnfvn168MEH1a1bN7Vr185K8Hl5eZLOnLA5d+5cde7cWQcOHLD2JO3atUsfffSR3n33XQ0aNEh169ZVvXr1JMlazvDwcC1ZskQPPfSQVUPz5s01fvx4pxNDb7rpJutEV+nMX3lycnJUs2ZNGWP066+/SjrzFxZjjDw8PKy/dNjtdhnuNw0AAFBpnH0BkOI4LhYSFxcnb29v7dmzR/PmzdOtt96q1q1bW/1iY2Pl6+srSQoLC1PNmjVlt9uVnp6uOnXqqH///oqJiVFWVpb69OmjpKQkxcbG6sYbb5TNZtPUqVM1ZMgQvfzyy7LZbMrMzNRDDz2kN954Q6dOnVJSUpKOHj2qq666SgkJCTp16pSefPJJa/5vv/22pDPbnadOndI111yjL774Qn379tWyZctUo0YNHTp0SAkJCcrNzdU///lP3XjjjYqIiFBgYKCuv/56SdKkSZN04sQJbd68WR999JHmz5+vvLw8a8/ioEGDdPLkSWuP5dKlS7V7926dOHFCEyZMUEJCgoYOHao6deooOjpavr6+ioqKUn5+vjw8PLRnzx517dpV0pnsULt2bUVFRenll19W+/btFRUVpezsbM2ZM0dt27ZVjx499N///tdazl9++UXLly/XypUrtXLlSm3YsEFPP/209XxycrLeeOMNzZ07Vzt37tQDDzygm2++2WlPpiQ9/PDDevrpp7Vr1y61bNmyVO+FMu/Z8vT0NAEBAdYeGg8PD/P++++XOF7fvn3Ngw8+aD127Nl6+eWXTXBwsFm/fr313Jtvvmni4uKcjuXMyckxfn5+ZtWqVcYYY6ZPn26aNGli1dShQwerpt9++83ExcUZLy8vc+TIEZOYmOh0zpbjJExvb2/z22+/me+++85K5ddee6257LLLTPfu3U1+fr7p1KmTmTVrlomNjTVeXl7WiZOOvXL/+te/rHRep04ds3DhQmtvmJeXl4mNjTVPPfWUleq7d+9uGjVqZLy9va3UriL+OkCj0Wg0Go1Gu7iaY3tPOnOuv7e3txkyZIiJi4szkkxoaKgxxpgbbrjBSDIdO3Y0v/32mzXOmjVrTK1atYyvr6+1zXnzzTc7HVXm2EuzadMmY7PZTLVq1aznoqKizIABA6zH7733nvHx8TF+fn7Gx8fH2nb39PQ0vr6+Jj093dobt2zZMvPmm2+aOnXqmNjYWGs7/KqrrjJeXl7Gx8fH2g5PSkoykZGRJioqyjpf7tFHHzU2m83Ur1/faRkd54CNHj3a+Pv7W9vJx44dM7179zaSTOvWrU12drbx9/c3mzdvNklJSaZmzZomKyvLhIeHm5CQEDNnzhyr1saNGxsvLy+zefNms3HjRhMUFGSys7PNbbfdZgYPHmyMMaZx48bm1VdftdaZv7+/056scePGmcsvv9wYY5zmXVDB6Tn2bC1fvrzEzFOU0sXzArp166Y5c+YoKytLM2fOlJeXl2644Qbr+by8PD311FN699139ccffyg3N1c5OTny9/d3ms7777+vw4cPa9OmTerQoYM1/Pvvv9fevXsLHeeanZ2tX375RdKZS4A++uij+vLLLyVJ+/fv16BBg3T8+HEtWrRIsbGx+vnnn5WYmKijR48qLi7Omo7jXC0vLy/FxsY67T3KyclRdHS0Nm/erIYNG2r//v2SpF9//VWnT59WRkaGJOmVV17R66+/bh2reeLECeXk5GjixIk6deqUJOn06dM6cOCAHn/8cWuv2eeff678/Hzl5+erdu3aOnr0qCQpOjpav/76q2w2m7XnzdfXV/n5+U7H2wIAAKDy8ff3t7YbJenQoUOy2Wx69913rW27o0ePas+ePdq8ebOkM9u8TZo0scZp2bKlcnNzFRsbq1q1amndunXWeXGZmZmaMmWKFi1apP/+97+68sorJcnp6LK///5bP/zwgyIiIpSRkaHTp08rNzdXwcHBuvfeezVkyBB16tRJ3bp103/+8x998MEHCgoKsubx/fff6+DBg0pLS7NuH1SQYzvcoVmzZtZRZbt371bt2rX1xx9/6ODBg/rkk0/k6empFi1aWP0bNGignJwcazrBwcGSpH79+mnv3r06efKkrr76auXk5MgYo9DQUJ08eVIhISGKj4+36gwLC9Mvv/yiq6++WqdOnVJubq61d9DDw0MfffSR/v77b6d6GzRo4JQt6tSpo8OHD0uS07wLys3NVZs2bZyGtW/fvtB6OZcyH0YYEBCg6OhotWrVSgsWLNBXX32l+fPnW8/PmDFDL7zwgh566CGtW7dOKSkp1q7Hgtq0aaOQkBAtWLDAKfBkZmaqXbt2SklJcWo///yzhgwZIkkKDQ1Vv379tHDhQv399986fPiwRowYoREjRmjRokXavn27Fi5cqFtuuUUZGRn6+OOP9dJLL0k6c5igJI0dO1a1a9e2LpjhUKtWLaWmpqply5Yyxmjz5s1WqHJ8WBITE5WSkmLtfvTw8JDdbtcNN9xgveltNptyc3M1depUK+zdeeedat++vVq1auV04YtOnTrJ39/f6aRAx25TAAAAVF7NmzeXMUb9+vVzGt6rVy/169fPugCbzWZTz549deLECUlnDod76623rP6Oe5IV5NhG/uc//6lly5apR48eql+/vi6//HLZbDbrYhW//fabDh8+rHr16umDDz7Q1q1brQu4GWNUu3ZtNW3aVDfeeKP27Nkjm82mJUuWaNCgQda8MjMzFRISopYtW2rNmjVas2aNWrZsqeuuu07fffedtR1esF4Hu90uHx8f+fv7a/DgwYqMjCy0LAX7O9aH41/HBVU++eQT9evXT+3bt1dKSoo6dOiga6+9tsj1/sknn+j+++9XWFiYVe/69euVkpKi3bt3a9y4cSXO++yLuXzyySdO2ePHH3/U+++/7zReURcHOZcL2pr38PDQxIkT9eijj1p7jDZt2qTExETdfPPNatWqlRo1aqSff/650LiNGzfWunXrtGLFCt13333W8LZt22rPnj0KDQ1VdHS0U3MkYEm6/fbb9c477+jnn39WQECArrzySuu8rlOnTunmm2/WXXfdpY4dO6pZs2Z67bXXlJ2dbdX5wAMPSFKRe478/f2tvWYPPvigNbxnz56SzgS26Oho61yu/Px8DR48WO3atbMCkuPD8X//93/W//fu3avU1FTl5+crMzPTGv7555/L09PTKXSyVwsAAMB97HZ7qfr98ssvysnJUaNGjaxhjiOogoKCrPPxO3bsqP3791sb+Y0aNSp0JJfj/K7t27c7Dd+0aZOGDx+uJk2aqHr16ho3bpyMMTp+/LhOnDihrVu3SjqzQ+CKK65QbGys/vzzT0nO27pDhw7Vrl27lJeXp//85z8aOnSo9Vzbtm2VmZmp/fv3q0OHDurRo4dq1Kih+vXrq02bNtZ2uI+PT6HrCsTExOjIkSMKCQnR+vXrdfPNN+v06dNOy5GXl6cDBw4UWn9r165V06ZNZbfbtX//fgUFBWnPnj2KiIiQn5+fqlWrpi+//NLaexUYGCgPDw/t379f11xzjf766y81btxYPXr00FVXXWXlhtq1a5fi1ZPTvM/OHpGRkaWaRkkueNfJwIED5enpaaXnmJgYrV69Wps3b9auXbt055136tChQ0WOGxsbq3Xr1umDDz6w7vw9dOhQ1a5dW4mJidq4caNSU1O1fv163X///fr999+tcRMSEhQUFKQffvjB+ouBp6endu3apX79+mnNmjVKTU3V8ePHdfDgQTVp0kR2u906sXHfvn2aO3duocu979y5Uw899JCOHTum4OBgLV++XHa7XVFRUVqzZo3VZ9KkSVq6dKkkyc/PT5988ol2795tfYBsNpvq1Kmj9evXa/fu3ZKkVatW6a+//tKuXbuUm5trBbPGjRtbf+VwOH36dJkufwkAAIDy4zgNpKCibsnj7e2t/Px8zZkzxxqWl5enb775RseOHbOOjPr+++8lybpE/CuvvKJHHnnEGmfNmjXy8fGRzWbTsWPHJElZWVnat2+fAgMDtXTpUm3fvl2///67Bg0aJE9PTwUEBKh3796qW7euJGnjxo369ddf9eabb2ru3LmSzpyKs27dOu3Zs0c//PCDjDE6efKkGjZsqMsvv9ya/9ChQ1W3bl3l5OSoS5cueuedd3To0CGtXLlSI0aMsLbDGzRooGPHjunEiRPWRSh69+4tf39//fXXX1q5cqVuuukmdejQQRMnTpQkHTlyRPv27SsyAH3zzTd66KGHdMstt+j+++/Xxo0b9ffff+u6665TamqqPv/8c02ePFnXXXedpDNBtnnz5nrggQf0xx9/qE2bNkpISNA999yjZ599Vps3b9Yjjzyib7/99twvsqRq1arpn//8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\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [],
      "metadata": {
        "id": "rMkFAhFHqzMg"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "Load the review data into a DataFrame and do some exploratory "
      ],
      "metadata": {
        "id": "S_gEn0Cuq6qB"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "movie_reviews =pd.read_csv('/content/rt.reviews.tsv', delimiter='\\t',  encoding='latin-1')\n",
        "movie_reviews.head()"
      ],
      "metadata": {
        "id": "I4mNfpxLrw74",
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 206
        },
        "outputId": "8edfbed6-7a98-413b-c3ae-122b30d6f35b"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "   id                                             review rating   fresh  \\\n",
              "0   3  A distinctly gallows take on contemporary fina...    3/5   fresh   \n",
              "1   3  It's an allegory in search of a meaning that n...    NaN  rotten   \n",
              "2   3  ... life lived in a bubble in financial dealin...    NaN   fresh   \n",
              "3   3  Continuing along a line introduced in last yea...    NaN   fresh   \n",
              "4   3             ... a perverse twist on neorealism...     NaN   fresh   \n",
              "\n",
              "           critic  top_critic         publisher               date  \n",
              "0      PJ Nabarro           0   Patrick Nabarro  November 10, 2018  \n",
              "1  Annalee Newitz           0           io9.com       May 23, 2018  \n",
              "2    Sean Axmaker           0  Stream on Demand    January 4, 2018  \n",
              "3   Daniel Kasman           0              MUBI  November 16, 2017  \n",
              "4             NaN           0      Cinema Scope   October 12, 2017  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-ab19f5a6-41da-4cbb-b225-ac11e2a00964\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>id</th>\n",
              "      <th>review</th>\n",
              "      <th>rating</th>\n",
              "      <th>fresh</th>\n",
              "      <th>critic</th>\n",
              "      <th>top_critic</th>\n",
              "      <th>publisher</th>\n",
              "      <th>date</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>3</td>\n",
              "      <td>A distinctly gallows take on contemporary fina...</td>\n",
              "      <td>3/5</td>\n",
              "      <td>fresh</td>\n",
              "      <td>PJ Nabarro</td>\n",
              "      <td>0</td>\n",
              "      <td>Patrick Nabarro</td>\n",
              "      <td>November 10, 2018</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>3</td>\n",
              "      <td>It's an allegory in search of a meaning that n...</td>\n",
              "      <td>NaN</td>\n",
              "      <td>rotten</td>\n",
              "      <td>Annalee Newitz</td>\n",
              "      <td>0</td>\n",
              "      <td>io9.com</td>\n",
              "      <td>May 23, 2018</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>3</td>\n",
              "      <td>... life lived in a bubble in financial dealin...</td>\n",
              "      <td>NaN</td>\n",
              "      <td>fresh</td>\n",
              "      <td>Sean Axmaker</td>\n",
              "      <td>0</td>\n",
              "      <td>Stream on Demand</td>\n",
              "      <td>January 4, 2018</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>3</td>\n",
              "      <td>Continuing along a line introduced in last yea...</td>\n",
              "      <td>NaN</td>\n",
              "      <td>fresh</td>\n",
              "      <td>Daniel Kasman</td>\n",
              "      <td>0</td>\n",
              "      <td>MUBI</td>\n",
              "      <td>November 16, 2017</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>3</td>\n",
              "      <td>... a perverse twist on neorealism...</td>\n",
              "      <td>NaN</td>\n",
              "      <td>fresh</td>\n",
              "      <td>NaN</td>\n",
              "      <td>0</td>\n",
              "      <td>Cinema Scope</td>\n",
              "      <td>October 12, 2017</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-ab19f5a6-41da-4cbb-b225-ac11e2a00964')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-ab19f5a6-41da-4cbb-b225-ac11e2a00964 button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-ab19f5a6-41da-4cbb-b225-ac11e2a00964');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 26
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "movie_reviews['fresh'].value_counts()"
      ],
      "metadata": {
        "id": "Su4CdfzqJG87",
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "outputId": "ee5b42f7-5453-41c5-83ef-e4c5e01a91f8"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "fresh     33035\n",
              "rotten    21397\n",
              "Name: fresh, dtype: int64"
            ]
          },
          "metadata": {},
          "execution_count": 27
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Load the tmdb movie\n",
        " data into a DataFrame and do some exploratory"
      ],
      "metadata": {
        "id": "D7YgHjIast_Y"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "mdb_movies = pd.read_csv('/content/tmdb.movies.csv',index_col=0)\n",
        "mdb_movies.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 285
        },
        "id": "WLY2m952s-SX",
        "outputId": "5b7cd74d-675e-4621-a543-d2872660e9e5"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "             genre_ids     id original_language  \\\n",
              "0      [12, 14, 10751]  12444                en   \n",
              "1  [14, 12, 16, 10751]  10191                en   \n",
              "2        [12, 28, 878]  10138                en   \n",
              "3      [16, 35, 10751]    862                en   \n",
              "4        [28, 878, 12]  27205                en   \n",
              "\n",
              "                                 original_title  popularity release_date  \\\n",
              "0  Harry Potter and the Deathly Hallows: Part 1      33.533   2010-11-19   \n",
              "1                      How to Train Your Dragon      28.734   2010-03-26   \n",
              "2                                    Iron Man 2      28.515   2010-05-07   \n",
              "3                                     Toy Story      28.005   1995-11-22   \n",
              "4                                     Inception      27.920   2010-07-16   \n",
              "\n",
              "                                          title  vote_average  vote_count  \n",
              "0  Harry Potter and the Deathly Hallows: Part 1           7.7       10788  \n",
              "1                      How to Train Your Dragon           7.7        7610  \n",
              "2                                    Iron Man 2           6.8       12368  \n",
              "3                                     Toy Story           7.9       10174  \n",
              "4                                     Inception           8.3       22186  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-06e4f6d7-dfbd-46be-84da-31bb214b163d\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>genre_ids</th>\n",
              "      <th>id</th>\n",
              "      <th>original_language</th>\n",
              "      <th>original_title</th>\n",
              "      <th>popularity</th>\n",
              "      <th>release_date</th>\n",
              "      <th>title</th>\n",
              "      <th>vote_average</th>\n",
              "      <th>vote_count</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>[12, 14, 10751]</td>\n",
              "      <td>12444</td>\n",
              "      <td>en</td>\n",
              "      <td>Harry Potter and the Deathly Hallows: Part 1</td>\n",
              "      <td>33.533</td>\n",
              "      <td>2010-11-19</td>\n",
              "      <td>Harry Potter and the Deathly Hallows: Part 1</td>\n",
              "      <td>7.7</td>\n",
              "      <td>10788</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>[14, 12, 16, 10751]</td>\n",
              "      <td>10191</td>\n",
              "      <td>en</td>\n",
              "      <td>How to Train Your Dragon</td>\n",
              "      <td>28.734</td>\n",
              "      <td>2010-03-26</td>\n",
              "      <td>How to Train Your Dragon</td>\n",
              "      <td>7.7</td>\n",
              "      <td>7610</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>[12, 28, 878]</td>\n",
              "      <td>10138</td>\n",
              "      <td>en</td>\n",
              "      <td>Iron Man 2</td>\n",
              "      <td>28.515</td>\n",
              "      <td>2010-05-07</td>\n",
              "      <td>Iron Man 2</td>\n",
              "      <td>6.8</td>\n",
              "      <td>12368</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>[16, 35, 10751]</td>\n",
              "      <td>862</td>\n",
              "      <td>en</td>\n",
              "      <td>Toy Story</td>\n",
              "      <td>28.005</td>\n",
              "      <td>1995-11-22</td>\n",
              "      <td>Toy Story</td>\n",
              "      <td>7.9</td>\n",
              "      <td>10174</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>[28, 878, 12]</td>\n",
              "      <td>27205</td>\n",
              "      <td>en</td>\n",
              "      <td>Inception</td>\n",
              "      <td>27.920</td>\n",
              "      <td>2010-07-16</td>\n",
              "      <td>Inception</td>\n",
              "      <td>8.3</td>\n",
              "      <td>22186</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-06e4f6d7-dfbd-46be-84da-31bb214b163d')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-06e4f6d7-dfbd-46be-84da-31bb214b163d button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-06e4f6d7-dfbd-46be-84da-31bb214b163d');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 28
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "top_language = mdb_movies['original_language'].unique()[:10]\n",
        "top_language_count = mdb_movies['original_language'].value_counts().nlargest(10).tolist()\n",
        "#top_language_sum = mdb_movies('top_language_count').sum()[:10]\n",
        "#top_language_percentage = top_language_sum / top_language_count = mdb_movies *100\n",
        "print(\"Language:\", top_language)\n",
        "\n",
        "print(\"Counts:\", top_language_count)\n",
        "\n",
        "\n",
        "\n"
      ],
      "metadata": {
        "id": "n25d7PFFtgRg",
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "outputId": "0b3e31a4-7cc2-441b-d09c-d6cc3b3d58ea"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Language: ['en' 'nl' 'es' 'ja' 'sv' 'de' 'fr' 'cn' 'it' 'ru']\n",
            "Counts: [23291, 507, 455, 298, 265, 237, 177, 172, 123, 96]\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "bar_chart_title = \"Top 10 Original Movie Language\"\n",
        "\n",
        "fig, ax = plt.subplots()\n",
        "\n",
        "\n",
        "ax.bar(top_language,top_language_count)\n",
        "ax.set_xlabel('Language')\n",
        "ax.set_ylabel('Count of Language Movies')\n",
        "ax.set_title(bar_chart_title)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 489
        },
        "id": "HPVaTGrDHpWU",
        "outputId": "b4971bef-0de6-4f82-8622-d07c3e574340"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "Text(0.5, 1.0, 'Top 10 Original Movie Language')"
            ]
          },
          "metadata": {},
          "execution_count": 73
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "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lZKnp6eKFi2qt99+W7GxsbJYLPruu+/UoEED+fj4qEqVKoqOjnZ25AzSD8/Vr19fJ06c0KBBg2SxWFzyO04zez/ceRg3ISFBFovFpd7b9qA05UATJkzQ119/renTp2v//v0aNGiQ/vWvf2njxo3WOSNHjtSkSZP022+/KVeuXOrZs6cTE2c0e/Zs+fr6auvWrZo4caLGjx+vNWvWODvWXd3rNX/jjTd04MAB/fjjjzp48KCmTZvm0oc1rly5osGDB+u3335TVFSU3Nzc9NxzzyktLc3Z0SRJp0+fVqdOndSzZ08dPHhQGzZsUNu2bVW/fn0FBgZq8eLF1rmpqamaP3++unTp4sTEf3vttde0ceNGLV26VD/99JM2bNig33//3bq8b9++io6O1rx587Rnzx516NBBzZo105EjR5yY+v9MnTpV48ePV5EiRXT69Glt375d0t//rXp4eGjz5s2aPn26k1PaGjFihN555x3rf4Nz5861+YaHkSNHaujQodq1a5fKlCmjTp066datW05MfHffffedihQpovHjx+v06dM6ffq0syNlypXfDw5hIEe5fv264ePjY2zZssVmvFevXkanTp2M9evXG5KMtWvXWpetXLnSkGRcu3btUcfNVL169Yw6derYjD3xxBPGsGHDDMMwDEnG999/74Rkmbvfa96qVSujR48eTkpnTrdu3Yxnn30202Xnzp0zJBl79+59tKHuYseOHYYkIzY2NsOyAQMGGA0bNrTeX716teHp6WlcunTpESbM6PLly4aHh4exYMEC69iFCxcMb29vY8CAAcaJEycMd3d349SpUzaPa9SokTFixIhHHfeupkyZYoSFhVnv16tXz3j88cedF+gekpKSDE9PT+Pzzz/PsOz48eOGJOOLL76wju3fv9+QZBw8ePBRxryvevXqGQMGDDAMwzDCwsKMKVOmODXPvdz5fkh/nXfu3Gkdu3TpkiHJWL9+/aMP6ACc05TDHD16VFevXlWTJk1sxm/cuKHHH3/cer9y5crWfxcuXFiSdPbsWRUtWvTRBL2P2/NJf2c8e/ask9Lc2/1e87Fjx6pdu3b6/fff1bRpU7Vp0+au54S4giNHjmj06NHaunWrzp8/b93DFBcXp4oVKzo5nVSlShU1atRIlSpVUmRkpJo2bar27dsrb9686tKli2rXrq2//vpLISEhmjNn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ZgCOxZ4mANnWjh07lJaWpkmTJsnN7e+/ARcsWGDXOgICAhQUFKTt27erbt26kv7es/P777+ratWq1nkFCxa0OXk8KSlJx48ftytLeHi4tm/fbjN25/1q1arp0KFDKlWqlF3PA0DWozQByBYSExO1a9cum7ECBQro5s2b+uijj9SqVStt3rxZ06dPt3vd/fr104QJE1SqVCmVLVtWH330kS5duiSLxWKd07BhQ82aNUutWrVSYGCgRo8eLXd3d+vyUqVK3TdLv379VLduXU2ePFmtWrXSunXr9OOPP9psZ/To0WrZsqWKFi2q9u3by83NTbt379a+ffv01ltv2f3cADgOh+cAZAsbNmzQ448/bnP75ptvNHnyZL377ruqWLGi5syZowkTJti97mHDhqlTp07q2rWrIiIi5Ofnp8jISJvDYSNGjFC9evXUsmVLtWjRQm3atLE5T6pKlSr3zfLUU09p+vTpmjx5sqpUqaJVq1Zp0KBBNtuJjIzUihUr9NNPP+mJJ55Q7dq1NWXKFIWFhT3AqwbAkSyGvQf2ASCHS0tLU7ly5fT888/rzTffzNJt9e7dWzExMfr555+zdDsAHh6H5wD84504cUI//fST6tWrp5SUFH388cc6fvy4Onfu7PBtvf/++2rSpIl8fX31448/avbs2fr0008dvh0AjkdpAvCP5+bmplmzZmno0KEyDEMVK1bU2rVrVa5cOYdva9u2bZo4caIuX76sEiVK6MMPP9S///1vh28HgONxeA4AAMAETgQHAAAwgdIEAABgAqUJAADABEoTAACACZQmAAAAEyhNAAAAJlCaAAAATKA0AQAAmEBpAgAAMOH/A03YVwsoHnuYAAAAAElFTkSuQmCC\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "none_english "
      ],
      "metadata": {
        "id": "5qizpN9En56h"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "mdb_movies['genre_ids'].unique"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "AIXZOJ7NmeUm",
        "outputId": "715d6837-0a01-46ca-f8ec-6643c32f51b6"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "<bound method Series.unique of 0            [12, 14, 10751]\n",
              "1        [14, 12, 16, 10751]\n",
              "2              [12, 28, 878]\n",
              "3            [16, 35, 10751]\n",
              "4              [28, 878, 12]\n",
              "                ...         \n",
              "26512               [27, 18]\n",
              "26513               [18, 53]\n",
              "26514           [14, 28, 12]\n",
              "26515        [10751, 12, 28]\n",
              "26516               [53, 27]\n",
              "Name: genre_ids, Length: 26517, dtype: object>"
            ]
          },
          "metadata": {},
          "execution_count": 31
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "mdb_movies.isna().sum()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "GWtXazgjeY65",
        "outputId": "5e6d3cf3-f450-459d-dcff-00de8b3127d9"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "genre_ids            0\n",
              "id                   0\n",
              "original_language    0\n",
              "original_title       0\n",
              "popularity           0\n",
              "release_date         0\n",
              "title                0\n",
              "vote_average         0\n",
              "vote_count           0\n",
              "dtype: int64"
            ]
          },
          "metadata": {},
          "execution_count": 32
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "mdb_movies.shape"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "o3kPPW7L6sFg",
        "outputId": "51de59db-0972-4ce0-8c85-6e9b59adf69d"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "(26517, 9)"
            ]
          },
          "metadata": {},
          "execution_count": 33
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "mdb_movies.duplicated().value_counts()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "dK65jgPksN0o",
        "outputId": "88acd8a0-11d2-43b7-b35b-1ddc331e24be"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "False    25497\n",
              "True      1020\n",
              "dtype: int64"
            ]
          },
          "metadata": {},
          "execution_count": 34
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Load the movie budgetdata into a DataFrame and do some exploratory."
      ],
      "metadata": {
        "id": "qAvm7Mnxtqmw"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "#Load the csv data\n",
        "movie_budget = pd.read_csv('/content/tn.movie_budgets.csv',index_col=0)\n",
        "movie_budget.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 237
        },
        "id": "8le6_hL9twVG",
        "outputId": "cdb94d7a-52d7-4d8f-ad88-b144f1b0f19e"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "    release_date                                        movie  \\\n",
              "id                                                              \n",
              "1   Dec 18, 2009                                       Avatar   \n",
              "2   May 20, 2011  Pirates of the Caribbean: On Stranger Tides   \n",
              "3    Jun 7, 2019                                 Dark Phoenix   \n",
              "4    May 1, 2015                      Avengers: Age of Ultron   \n",
              "5   Dec 15, 2017            Star Wars Ep. VIII: The Last Jedi   \n",
              "\n",
              "   production_budget domestic_gross worldwide_gross  \n",
              "id                                                   \n",
              "1       $425,000,000   $760,507,625  $2,776,345,279  \n",
              "2       $410,600,000   $241,063,875  $1,045,663,875  \n",
              "3       $350,000,000    $42,762,350    $149,762,350  \n",
              "4       $330,600,000   $459,005,868  $1,403,013,963  \n",
              "5       $317,000,000   $620,181,382  $1,316,721,747  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-b8e42d3d-0f19-47b0-846a-623b1bda78eb\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>release_date</th>\n",
              "      <th>movie</th>\n",
              "      <th>production_budget</th>\n",
              "      <th>domestic_gross</th>\n",
              "      <th>worldwide_gross</th>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>id</th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>Dec 18, 2009</td>\n",
              "      <td>Avatar</td>\n",
              "      <td>$425,000,000</td>\n",
              "      <td>$760,507,625</td>\n",
              "      <td>$2,776,345,279</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>May 20, 2011</td>\n",
              "      <td>Pirates of the Caribbean: On Stranger Tides</td>\n",
              "      <td>$410,600,000</td>\n",
              "      <td>$241,063,875</td>\n",
              "      <td>$1,045,663,875</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>Jun 7, 2019</td>\n",
              "      <td>Dark Phoenix</td>\n",
              "      <td>$350,000,000</td>\n",
              "      <td>$42,762,350</td>\n",
              "      <td>$149,762,350</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>May 1, 2015</td>\n",
              "      <td>Avengers: Age of Ultron</td>\n",
              "      <td>$330,600,000</td>\n",
              "      <td>$459,005,868</td>\n",
              "      <td>$1,403,013,963</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>5</th>\n",
              "      <td>Dec 15, 2017</td>\n",
              "      <td>Star Wars Ep. VIII: The Last Jedi</td>\n",
              "      <td>$317,000,000</td>\n",
              "      <td>$620,181,382</td>\n",
              "      <td>$1,316,721,747</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-b8e42d3d-0f19-47b0-846a-623b1bda78eb')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-b8e42d3d-0f19-47b0-846a-623b1bda78eb button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-b8e42d3d-0f19-47b0-846a-623b1bda78eb');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 35
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "movie_budget.dtypes"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "aqClyEvjumM0",
        "outputId": "efe9c72f-9b65-4ecc-b0c8-8d66cec8f225"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "release_date         object\n",
              "movie                object\n",
              "production_budget    object\n",
              "domestic_gross       object\n",
              "worldwide_gross      object\n",
              "dtype: object"
            ]
          },
          "metadata": {},
          "execution_count": 36
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#convert the release date data into datetime\n",
        "movie_budget['release_date'] =  pd.to_datetime(movie_budget['release_date'])\n",
        "movie_budget['release_date'].describe()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "Y1p5v1TCvYdC",
        "outputId": "7ab3374d-90df-4a9f-e882-48040d6331d6"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "<ipython-input-37-dfb959834d69>:3: FutureWarning: Treating datetime data as categorical rather than numeric in `.describe` is deprecated and will be removed in a future version of pandas. Specify `datetime_is_numeric=True` to silence this warning and adopt the future behavior now.\n",
            "  movie_budget['release_date'].describe()\n"
          ]
        },
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "count                    5782\n",
              "unique                   2418\n",
              "top       2014-12-31 00:00:00\n",
              "freq                       24\n",
              "first     1915-02-08 00:00:00\n",
              "last      2020-12-31 00:00:00\n",
              "Name: release_date, dtype: object"
            ]
          },
          "metadata": {},
          "execution_count": 37
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#Remove the characters using a function.Example $ and ,\n",
        "def remove_character(data, cols, characters):\n",
        "    \"\"\"simple function to remove characters\"\"\"\n",
        "    # loop through the columns\n",
        "    for col in cols:\n",
        "        data[col] = data[col].str.strip(characters)\n",
        "\n",
        "    return data.head()\n",
        "\n",
        "remove_character(movie_budget, ['production_budget', 'domestic_gross', 'worldwide_gross'],'$')"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 237
        },
        "id": "kK2XtiTDyim3",
        "outputId": "225f4fdf-3790-4a5b-ce9e-6e0d7268f9d2"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "   release_date                                        movie  \\\n",
              "id                                                             \n",
              "1    2009-12-18                                       Avatar   \n",
              "2    2011-05-20  Pirates of the Caribbean: On Stranger Tides   \n",
              "3    2019-06-07                                 Dark Phoenix   \n",
              "4    2015-05-01                      Avengers: Age of Ultron   \n",
              "5    2017-12-15            Star Wars Ep. VIII: The Last Jedi   \n",
              "\n",
              "   production_budget domestic_gross worldwide_gross  \n",
              "id                                                   \n",
              "1        425,000,000    760,507,625   2,776,345,279  \n",
              "2        410,600,000    241,063,875   1,045,663,875  \n",
              "3        350,000,000     42,762,350     149,762,350  \n",
              "4        330,600,000    459,005,868   1,403,013,963  \n",
              "5        317,000,000    620,181,382   1,316,721,747  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-f60036e1-410d-4c32-9a67-f697969e48b2\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>release_date</th>\n",
              "      <th>movie</th>\n",
              "      <th>production_budget</th>\n",
              "      <th>domestic_gross</th>\n",
              "      <th>worldwide_gross</th>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>id</th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>2009-12-18</td>\n",
              "      <td>Avatar</td>\n",
              "      <td>425,000,000</td>\n",
              "      <td>760,507,625</td>\n",
              "      <td>2,776,345,279</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>2011-05-20</td>\n",
              "      <td>Pirates of the Caribbean: On Stranger Tides</td>\n",
              "      <td>410,600,000</td>\n",
              "      <td>241,063,875</td>\n",
              "      <td>1,045,663,875</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>2019-06-07</td>\n",
              "      <td>Dark Phoenix</td>\n",
              "      <td>350,000,000</td>\n",
              "      <td>42,762,350</td>\n",
              "      <td>149,762,350</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>2015-05-01</td>\n",
              "      <td>Avengers: Age of Ultron</td>\n",
              "      <td>330,600,000</td>\n",
              "      <td>459,005,868</td>\n",
              "      <td>1,403,013,963</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>5</th>\n",
              "      <td>2017-12-15</td>\n",
              "      <td>Star Wars Ep. VIII: The Last Jedi</td>\n",
              "      <td>317,000,000</td>\n",
              "      <td>620,181,382</td>\n",
              "      <td>1,316,721,747</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-f60036e1-410d-4c32-9a67-f697969e48b2')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-f60036e1-410d-4c32-9a67-f697969e48b2 button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-f60036e1-410d-4c32-9a67-f697969e48b2');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 38
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#movie_budget.dtypes"
      ],
      "metadata": {
        "id": "Vp5CJZklzR7j"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "#movie_budget.head()"
      ],
      "metadata": {
        "id": "a2_DytarIsJB"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "movie_budget['domestic_gross'] = movie_budget['domestic_gross'].str.replace(',','')\n",
        "movie_budget['domestic_gross'] = pd.to_numeric(movie_budget['domestic_gross'])\n"
      ],
      "metadata": {
        "id": "rOcmDHXFHJ2p"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "movie_budget['production_budget'] = movie_budget['production_budget'].str.replace(',','')\n",
        "movie_budget['production_budget'] = pd.to_numeric(movie_budget['production_budget'])\n"
      ],
      "metadata": {
        "id": "kYTszS53Tstu"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "movie_budget['worldwide_gross'] = movie_budget['worldwide_gross'].str.replace(',','')\n",
        "movie_budget['worldwide_gross'] = pd.to_numeric(movie_budget['worldwide_gross'])"
      ],
      "metadata": {
        "id": "GsVvxBCZnYUm"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "movie_budget['release_date'] = pd.to_datetime(movie_budget['release_date'])"
      ],
      "metadata": {
        "id": "OLS-o686Vt4D"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "movie_budget.info()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "VLj8FCAyo4a0",
        "outputId": "9225b163-eb00-4ad9-b5b6-a76c3cd6de2f"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "<class 'pandas.core.frame.DataFrame'>\n",
            "Int64Index: 5782 entries, 1 to 82\n",
            "Data columns (total 5 columns):\n",
            " #   Column             Non-Null Count  Dtype         \n",
            "---  ------             --------------  -----         \n",
            " 0   release_date       5782 non-null   datetime64[ns]\n",
            " 1   movie              5782 non-null   object        \n",
            " 2   production_budget  5782 non-null   int64         \n",
            " 3   domestic_gross     5782 non-null   int64         \n",
            " 4   worldwide_gross    5782 non-null   int64         \n",
            "dtypes: datetime64[ns](1), int64(3), object(1)\n",
            "memory usage: 271.0+ KB\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#CHECK THE DATAFRAME WITH THE ADDED COLUMNS(ADD THE COLUMNS)\n",
        "movie_budget['month'] = movie_budget['release_date'].dt.month\n",
        "movie_budget['year'] = movie_budget['release_date'].dt.year\n",
        "movie_budget['day'] = movie_budget['release_date'].dt.day\n",
        "movie_budget['total_gross'] = movie_budget[ 'domestic_gross']+ movie_budget['worldwide_gross']\n",
        "movie_budget['net_gross'] = movie_budget['total_gross']- movie_budget['production_budget']\n",
        "movie_budget.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 281
        },
        "id": "yq0-Fx9jUvVs",
        "outputId": "8305e296-ea14-4726-c2b6-6ce69e49bf7c"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "   release_date                                        movie  \\\n",
              "id                                                             \n",
              "1    2009-12-18                                       Avatar   \n",
              "2    2011-05-20  Pirates of the Caribbean: On Stranger Tides   \n",
              "3    2019-06-07                                 Dark Phoenix   \n",
              "4    2015-05-01                      Avengers: Age of Ultron   \n",
              "5    2017-12-15            Star Wars Ep. VIII: The Last Jedi   \n",
              "\n",
              "    production_budget  domestic_gross  worldwide_gross  month  year  day  \\\n",
              "id                                                                         \n",
              "1           425000000       760507625       2776345279     12  2009   18   \n",
              "2           410600000       241063875       1045663875      5  2011   20   \n",
              "3           350000000        42762350        149762350      6  2019    7   \n",
              "4           330600000       459005868       1403013963      5  2015    1   \n",
              "5           317000000       620181382       1316721747     12  2017   15   \n",
              "\n",
              "    total_gross   net_gross  \n",
              "id                           \n",
              "1    3536852904  3111852904  \n",
              "2    1286727750   876127750  \n",
              "3     192524700  -157475300  \n",
              "4    1862019831  1531419831  \n",
              "5    1936903129  1619903129  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-df33ae51-9c94-490d-b6fd-e818bad6389c\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>release_date</th>\n",
              "      <th>movie</th>\n",
              "      <th>production_budget</th>\n",
              "      <th>domestic_gross</th>\n",
              "      <th>worldwide_gross</th>\n",
              "      <th>month</th>\n",
              "      <th>year</th>\n",
              "      <th>day</th>\n",
              "      <th>total_gross</th>\n",
              "      <th>net_gross</th>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>id</th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "      <th></th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>2009-12-18</td>\n",
              "      <td>Avatar</td>\n",
              "      <td>425000000</td>\n",
              "      <td>760507625</td>\n",
              "      <td>2776345279</td>\n",
              "      <td>12</td>\n",
              "      <td>2009</td>\n",
              "      <td>18</td>\n",
              "      <td>3536852904</td>\n",
              "      <td>3111852904</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>2011-05-20</td>\n",
              "      <td>Pirates of the Caribbean: On Stranger Tides</td>\n",
              "      <td>410600000</td>\n",
              "      <td>241063875</td>\n",
              "      <td>1045663875</td>\n",
              "      <td>5</td>\n",
              "      <td>2011</td>\n",
              "      <td>20</td>\n",
              "      <td>1286727750</td>\n",
              "      <td>876127750</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>2019-06-07</td>\n",
              "      <td>Dark Phoenix</td>\n",
              "      <td>350000000</td>\n",
              "      <td>42762350</td>\n",
              "      <td>149762350</td>\n",
              "      <td>6</td>\n",
              "      <td>2019</td>\n",
              "      <td>7</td>\n",
              "      <td>192524700</td>\n",
              "      <td>-157475300</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>2015-05-01</td>\n",
              "      <td>Avengers: Age of Ultron</td>\n",
              "      <td>330600000</td>\n",
              "      <td>459005868</td>\n",
              "      <td>1403013963</td>\n",
              "      <td>5</td>\n",
              "      <td>2015</td>\n",
              "      <td>1</td>\n",
              "      <td>1862019831</td>\n",
              "      <td>1531419831</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>5</th>\n",
              "      <td>2017-12-15</td>\n",
              "      <td>Star Wars Ep. VIII: The Last Jedi</td>\n",
              "      <td>317000000</td>\n",
              "      <td>620181382</td>\n",
              "      <td>1316721747</td>\n",
              "      <td>12</td>\n",
              "      <td>2017</td>\n",
              "      <td>15</td>\n",
              "      <td>1936903129</td>\n",
              "      <td>1619903129</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-df33ae51-9c94-490d-b6fd-e818bad6389c')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-df33ae51-9c94-490d-b6fd-e818bad6389c button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-df33ae51-9c94-490d-b6fd-e818bad6389c');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 46
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#CHECK FOR STATISTICAK MEASUREMENT FOR THE COLUMNS WITH NUMERICAL DATA \n",
        "movie_budget_clean  = movie_budget\n",
        "#movie_budget_clean =['production_budget']\n",
        "movie_budget_clean.describe()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 300
        },
        "id": "1rk4wkC2VdZd",
        "outputId": "dbcbdd31-8286-4108-df93-28b2de2a6295"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "       production_budget  domestic_gross  worldwide_gross        month  \\\n",
              "count       5.782000e+03    5.782000e+03     5.782000e+03  5782.000000   \n",
              "mean        3.158776e+07    4.187333e+07     9.148746e+07     7.050675   \n",
              "std         4.181208e+07    6.824060e+07     1.747200e+08     3.480147   \n",
              "min         1.100000e+03    0.000000e+00     0.000000e+00     1.000000   \n",
              "25%         5.000000e+06    1.429534e+06     4.125415e+06     4.000000   \n",
              "50%         1.700000e+07    1.722594e+07     2.798445e+07     7.000000   \n",
              "75%         4.000000e+07    5.234866e+07     9.764584e+07    10.000000   \n",
              "max         4.250000e+08    9.366622e+08     2.776345e+09    12.000000   \n",
              "\n",
              "              year          day   total_gross     net_gross  \n",
              "count  5782.000000  5782.000000  5.782000e+03  5.782000e+03  \n",
              "mean   2003.967139    16.401245  1.333608e+08  1.017730e+08  \n",
              "std      12.724386     8.803660  2.399411e+08  2.108880e+08  \n",
              "min    1915.000000     1.000000  0.000000e+00 -1.574753e+08  \n",
              "25%    2000.000000     9.000000  6.448924e+06 -3.098222e+05  \n",
              "50%    2007.000000    17.000000  4.605855e+07  2.499538e+07  \n",
              "75%    2012.000000    24.000000  1.506937e+08  1.111648e+08  \n",
              "max    2020.000000    31.000000  3.536853e+09  3.111853e+09  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-faa621b7-805b-4442-8a10-1e23f298ef3e\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>production_budget</th>\n",
              "      <th>domestic_gross</th>\n",
              "      <th>worldwide_gross</th>\n",
              "      <th>month</th>\n",
              "      <th>year</th>\n",
              "      <th>day</th>\n",
              "      <th>total_gross</th>\n",
              "      <th>net_gross</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>count</th>\n",
              "      <td>5.782000e+03</td>\n",
              "      <td>5.782000e+03</td>\n",
              "      <td>5.782000e+03</td>\n",
              "      <td>5782.000000</td>\n",
              "      <td>5782.000000</td>\n",
              "      <td>5782.000000</td>\n",
              "      <td>5.782000e+03</td>\n",
              "      <td>5.782000e+03</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>mean</th>\n",
              "      <td>3.158776e+07</td>\n",
              "      <td>4.187333e+07</td>\n",
              "      <td>9.148746e+07</td>\n",
              "      <td>7.050675</td>\n",
              "      <td>2003.967139</td>\n",
              "      <td>16.401245</td>\n",
              "      <td>1.333608e+08</td>\n",
              "      <td>1.017730e+08</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>std</th>\n",
              "      <td>4.181208e+07</td>\n",
              "      <td>6.824060e+07</td>\n",
              "      <td>1.747200e+08</td>\n",
              "      <td>3.480147</td>\n",
              "      <td>12.724386</td>\n",
              "      <td>8.803660</td>\n",
              "      <td>2.399411e+08</td>\n",
              "      <td>2.108880e+08</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>min</th>\n",
              "      <td>1.100000e+03</td>\n",
              "      <td>0.000000e+00</td>\n",
              "      <td>0.000000e+00</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>1915.000000</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.000000e+00</td>\n",
              "      <td>-1.574753e+08</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>25%</th>\n",
              "      <td>5.000000e+06</td>\n",
              "      <td>1.429534e+06</td>\n",
              "      <td>4.125415e+06</td>\n",
              "      <td>4.000000</td>\n",
              "      <td>2000.000000</td>\n",
              "      <td>9.000000</td>\n",
              "      <td>6.448924e+06</td>\n",
              "      <td>-3.098222e+05</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>50%</th>\n",
              "      <td>1.700000e+07</td>\n",
              "      <td>1.722594e+07</td>\n",
              "      <td>2.798445e+07</td>\n",
              "      <td>7.000000</td>\n",
              "      <td>2007.000000</td>\n",
              "      <td>17.000000</td>\n",
              "      <td>4.605855e+07</td>\n",
              "      <td>2.499538e+07</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>75%</th>\n",
              "      <td>4.000000e+07</td>\n",
              "      <td>5.234866e+07</td>\n",
              "      <td>9.764584e+07</td>\n",
              "      <td>10.000000</td>\n",
              "      <td>2012.000000</td>\n",
              "      <td>24.000000</td>\n",
              "      <td>1.506937e+08</td>\n",
              "      <td>1.111648e+08</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>max</th>\n",
              "      <td>4.250000e+08</td>\n",
              "      <td>9.366622e+08</td>\n",
              "      <td>2.776345e+09</td>\n",
              "      <td>12.000000</td>\n",
              "      <td>2020.000000</td>\n",
              "      <td>31.000000</td>\n",
              "      <td>3.536853e+09</td>\n",
              "      <td>3.111853e+09</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-faa621b7-805b-4442-8a10-1e23f298ef3e')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-faa621b7-805b-4442-8a10-1e23f298ef3e button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-faa621b7-805b-4442-8a10-1e23f298ef3e');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 47
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "movie_budget_clean.duplicated().value_counts()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "C3-Xc9n1gRFg",
        "outputId": "b7df69ba-ba6c-4f2f-ccd8-42f0fae1f565"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "False    5782\n",
              "dtype: int64"
            ]
          },
          "metadata": {},
          "execution_count": 48
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "movie_budget_clean['production_budget'].corr(movie_budget_clean['month'])"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "5JJ6MV9CeafO",
        "outputId": "d584e8db-bbfd-4c0a-e4cd-0bc70d887499"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "0.02257524976931849"
            ]
          },
          "metadata": {},
          "execution_count": 49
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "movie_budget_clean.corr()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 355
        },
        "id": "AYOZGoyBe-hV",
        "outputId": "15bbf54f-a47b-46bc-d90e-23a8747a9d29"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "<ipython-input-50-765aa2c9200e>:1: FutureWarning: The default value of numeric_only in DataFrame.corr is deprecated. In a future version, it will default to False. Select only valid columns or specify the value of numeric_only to silence this warning.\n",
            "  movie_budget_clean.corr()\n"
          ]
        },
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                   production_budget  domestic_gross  worldwide_gross  \\\n",
              "production_budget           1.000000        0.685682         0.748306   \n",
              "domestic_gross              0.685682        1.000000         0.938853   \n",
              "worldwide_gross             0.748306        0.938853         1.000000   \n",
              "month                       0.022575        0.028034         0.030288   \n",
              "year                        0.176091        0.036690         0.100588   \n",
              "day                        -0.019217       -0.041380        -0.029274   \n",
              "total_gross                 0.739912        0.968058         0.995194   \n",
              "net_gross                   0.643580        0.965476         0.983933   \n",
              "\n",
              "                      month      year       day  total_gross  net_gross  \n",
              "production_budget  0.022575  0.176091 -0.019217     0.739912   0.643580  \n",
              "domestic_gross     0.028034  0.036690 -0.041380     0.968058   0.965476  \n",
              "worldwide_gross    0.030288  0.100588 -0.029274     0.995194   0.983933  \n",
              "month              1.000000 -0.020533  0.100438     0.030028   0.029689  \n",
              "year              -0.020533  1.000000  0.034229     0.083681   0.060296  \n",
              "day                0.100438  0.034229  1.000000    -0.033085  -0.033833  \n",
              "total_gross        0.030028  0.083681 -0.033085     1.000000   0.991066  \n",
              "net_gross          0.029689  0.060296 -0.033833     0.991066   1.000000  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-9210e1bb-b2cf-4bab-b49a-84714efec167\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>production_budget</th>\n",
              "      <th>domestic_gross</th>\n",
              "      <th>worldwide_gross</th>\n",
              "      <th>month</th>\n",
              "      <th>year</th>\n",
              "      <th>day</th>\n",
              "      <th>total_gross</th>\n",
              "      <th>net_gross</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>production_budget</th>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.685682</td>\n",
              "      <td>0.748306</td>\n",
              "      <td>0.022575</td>\n",
              "      <td>0.176091</td>\n",
              "      <td>-0.019217</td>\n",
              "      <td>0.739912</td>\n",
              "      <td>0.643580</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>domestic_gross</th>\n",
              "      <td>0.685682</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.938853</td>\n",
              "      <td>0.028034</td>\n",
              "      <td>0.036690</td>\n",
              "      <td>-0.041380</td>\n",
              "      <td>0.968058</td>\n",
              "      <td>0.965476</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>worldwide_gross</th>\n",
              "      <td>0.748306</td>\n",
              "      <td>0.938853</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.030288</td>\n",
              "      <td>0.100588</td>\n",
              "      <td>-0.029274</td>\n",
              "      <td>0.995194</td>\n",
              "      <td>0.983933</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>month</th>\n",
              "      <td>0.022575</td>\n",
              "      <td>0.028034</td>\n",
              "      <td>0.030288</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>-0.020533</td>\n",
              "      <td>0.100438</td>\n",
              "      <td>0.030028</td>\n",
              "      <td>0.029689</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>year</th>\n",
              "      <td>0.176091</td>\n",
              "      <td>0.036690</td>\n",
              "      <td>0.100588</td>\n",
              "      <td>-0.020533</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.034229</td>\n",
              "      <td>0.083681</td>\n",
              "      <td>0.060296</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>day</th>\n",
              "      <td>-0.019217</td>\n",
              "      <td>-0.041380</td>\n",
              "      <td>-0.029274</td>\n",
              "      <td>0.100438</td>\n",
              "      <td>0.034229</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>-0.033085</td>\n",
              "      <td>-0.033833</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>total_gross</th>\n",
              "      <td>0.739912</td>\n",
              "      <td>0.968058</td>\n",
              "      <td>0.995194</td>\n",
              "      <td>0.030028</td>\n",
              "      <td>0.083681</td>\n",
              "      <td>-0.033085</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.991066</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>net_gross</th>\n",
              "      <td>0.643580</td>\n",
              "      <td>0.965476</td>\n",
              "      <td>0.983933</td>\n",
              "      <td>0.029689</td>\n",
              "      <td>0.060296</td>\n",
              "      <td>-0.033833</td>\n",
              "      <td>0.991066</td>\n",
              "      <td>1.000000</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-9210e1bb-b2cf-4bab-b49a-84714efec167')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-9210e1bb-b2cf-4bab-b49a-84714efec167 button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-9210e1bb-b2cf-4bab-b49a-84714efec167');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 50
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#he Movie Industry had tremendously growth over the period with peaks experienced in the the mid 2000's\n",
        "sns.histplot(data = movie_budget_clean, x =\"year\",color =\"blue\",bins=12).set_title('Trend of the Annual Movie Releases from 1920 to 2020')\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 489
        },
        "id": "EqdZG2cmbm3O",
        "outputId": "fe4ab68d-c58d-4216-aff2-5157a5a9ba3f"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "Text(0.5, 1.0, 'Trend of the Annual Movie Releases from 1920 to 2020')"
            ]
          },
          "metadata": {},
          "execution_count": 51
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "iVBORw0KGgoAAAANSUhEUgAAAkQAAAHHCAYAAABeLEexAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjcuMSwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy/bCgiHAAAACXBIWXMAAA9hAAAPYQGoP6dpAABVWklEQVR4nO3deVxUVf8H8M+wDYsMiLIqIi4hoqKSEZWoYSCiZm65m5JaoqWW+vBkitYTueRSUmZPaovm0qKmhoKaS5IpSioiqUmYsogIIyD7+f3hj/t4BWQJmMH7eb9e89I598yZ7z0M8OHec2dUQggBIiIiIgUz0HUBRERERLrGQERERESKx0BEREREisdARERERIrHQERERESKx0BEREREisdARERERIrHQERERESKx0BEREREisdARA8VFhYGlUpVp2NGRkaia9euMDU1hUqlQlZWVo3HUKlUmD59ep3WpRStW7fGSy+9pOsyqu2ll15C69atdV3GQ23cuBEqlQpJSUm6LqXenTx5Ek899RQsLCygUqkQFxen65KI6gQDkY6oVKpq3X7++Wddl1qnbt26hREjRsDMzAwRERH46quvYGFhUWHf48ePIywsrFaBqa6VlJTAyckJKpUKP/30k67LaRBlr8GXX365wu1vvfWW1CcjI6OBq6u9spBfdjM2Nkbr1q3x2muv6cVrTZ8VFRVh+PDhyMzMxMqVK/HVV1/BxcVF12VVKicnBwsXLkS/fv1gY2MDlUqFjRs3Vtp/zZo1cHd3h1qtRosWLTB79mzk5ubK+ly8eBFz585F165dYWlpCUdHRwQFBeHUqVMVjnn9+nWMGDEC1tbW0Gg0eP755/Hnn39Wq/733nsPO3bsqO7uVsutW7ewbNky+Pr6wtbWFtbW1njyySexdevWCvsXFBRg3rx5cHJygpmZGby9vREVFSXrk5eXh4iICPj7+8PR0RGWlpbo1q0bPvnkE5SUlJQbs7S0FEuXLoWrqytMTU3RpUsXfPPNN3W6n7UiSCe++uor2e25554TAMq1p6am6rTOhQsXirp8mfz0008CgIiKiqqy77JlywQAcfXq1XLbAIiQkJA6q6sq+/fvFwBE69atxZgxYxrseeuDi4uLmDBhQpX9AAhTU1NhbW0tCgoKym13dXUVpqamAoC4efNmPVR6T2FhocjPz6+z8cpe05988on4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/vz5CAkJkY7yvPLKK1izZg3mzp2LSZMm4eDBg9i2bRv27Nmjs30nIiIi/aHTI0SffPIJsrOz0bt3bzg6Okq3rVu3Sn1WrlyJAQMGYOjQofD19YWDgwO+//57abuhoSF2794NQ0ND+Pj4YOzYsRg/fjwWL14s9XF1dcWePXsQFRUFT09PfPDBB/jvf/+LgICABt1fIiIi0k86PUJUnbdAMjU1RUREBCIiIirt4+Ligr179z50nN69e+PMmTM1rpGIiIgefXpzlRkRERGRrjAQERERkeIxEBEREZHiMRARERGR4jEQERERkeIxEBEREZHiMRARERGR4jEQERERkeIxEBEREZHiMRARERGR4jEQERERkeIxEBEREZHiMRARERGR4jEQERERkeIxEBEREZHiMRARERGR4jEQERERkeIxEBEREZHiMRARERGR4jEQERERkeIxEBEREZHiMRARERGR4jEQERERkeIxEBEREZHiMRARERGR4jEQERERkeIxEBEREZHiMRARERGR4jEQERERkeIxEBEREZHi6TQQHTlyBAMHDoSTkxNUKhV27Ngh265SqSq8LVu2TOrTunXrctvff/992Thnz55Fz549YWpqCmdnZyxdurQhdo+IiIgaCZ0GotzcXHh6eiIiIqLC7SkpKbLb+vXroVKpMHToUFm/xYsXy/rNmDFD2qbVauHv7w8XFxfExsZi2bJlCAsLw7p16+p134iIiKjxMNLlkwcGBiIwMLDS7Q4ODrL7O3fuRJ8+fdCmTRtZu6WlZbm+ZTZt2oTCwkKsX78eJiYm8PDwQFxcHFasWIEpU6b8850gIiKiRq/RrCFKS0vDnj17EBwcXG7b+++/j2bNmqFbt25YtmwZiouLpW0xMTHw9fWFiYmJ1BYQEIDExETcvn27wucqKCiAVquV3YiIiOjRpdMjRDXxxRdfwNLSEkOGDJG1v/baa+jevTtsbGxw/PhxhIaGIiUlBStWrAAApKamwtXVVfYYe3t7aVvTpk3LPVd4eDgWLVpUT3tCRERE+qbRBKL169djzJgxMDU1lbXPnj1b+n+XLl1gYmKCqVOnIjw8HGq1ulbPFRoaKhtXq9XC2dm5doUTERGR3msUgejo0aNITEzE1q1bq+zr7e2N4uJiJCUlwc3NDQ4ODkhLS5P1Kbtf2bojtVpd6zBFREREjU+jWEP0+eefw8vLC56enlX2jYuLg4GBAezs7AAAPj4+OHLkCIqKiqQ+UVFRcHNzq/B0GRERESmPTgNRTk4O4uLiEBcXBwC4evUq4uLikJycLPXRarXYvn07Xn755XKPj4mJwapVq/D777/jzz//xKZNmzBr1iyMHTtWCjujR4+GiYkJgoODER8fj61bt2L16tWyU2JERESkbDo9ZXbq1Cn06dNHul8WUiZMmICNGzcCALZs2QIhBEaNGlXu8Wq1Glu2bEFYWBgKCgrg6uqKWbNmycKOlZUV9u/fj5CQEHh5eaF58+ZYsGABL7knIiIiiUoIIXRdhL7TarWwsrJCdnY2NBqNrsshIqJG4PTp0/Dy8oKXVywsLbvruhwAwJ07pxEb64XY2Fh0764fNdWnmvz+bhRriIiIiIjqEwMRERERKR4DERERESkeAxEREREpHgMRERERKR4DERERESleo/joDiIiIqo7CQkJui6hnObNm6NVq1Y6e34GIiIiIoUoLEwBYICxY8fqupRyTE3NkZiYoLNQxEBERESkEMXFWQBK0br1Z2jWTH/emDEvLwEJCWORkZHBQEREREQNw8zMTW/ePVtfcFE1ERERKR4DERERESkeAxEREREpHgMRERERKR4DERERESkeAxEREREpHgMRERERKR4DERERESkeAxEREREpHgMRERERKR4DERERESkeAxEREREpHgMRERERKR4DERERESkeAxEREREpHgMRERERKR4DERERESkeAxEREREpHgMRERERKR4DERERESmeTgPRkSNHMHDgQDg5OUGlUmHHjh2y7S+99BJUKpXs1q9fP1mfzMxMjBkzBhqNBtbW1ggODkZOTo6sz9mzZ9GzZ0+YmprC2dkZS5cure9dIyIiokZEp4EoNzcXnp6eiIiIqLRPv379kJKSIt2++eYb2fYxY8YgPj4eUVFR2L17N44cOYIpU6ZI27VaLfz9/eHi4oLY2FgsW7YMYWFhWLduXb3tFxERETUuRrp88sDAQAQGBj60j1qthoODQ4XbEhISEBkZiZMnT+Lxxx8HAHz00Ufo378/li9fDicnJ2zatAmFhYVYv349TExM4OHhgbi4OKxYsUIWnIiIiEi59H4N0c8//ww7Ozu4ubnh1Vdfxa1bt6RtMTExsLa2lsIQAPTt2xcGBgY4ceKE1MfX1xcmJiZSn4CAACQmJuL2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\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#The last quarter of a calender year is the best time to release new movies.\n",
        "sns.histplot(x =\"month\",color =\"orange\",bins=12, data=movie_budget_clean).set_title('Number of Released Movies by Month')"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 489
        },
        "id": "DpWhoeo7wl3v",
        "outputId": "2af5f371-c4a1-4cc6-c974-b1f866c34109"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "Text(0.5, 1.0, 'Number of Released Movies by Month')"
            ]
          },
          "metadata": {},
          "execution_count": 52
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "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nnvu0VVXXaUTJ05o69at8vPz0zvvvHNZ+54+fbpee+01DRgwQJMmTVJAQIBefPFFHTt2TH//+98drq+pDXfffbceffRRLViwQIMHD9bYsWP1xhtv6He/+522bt2qXr16qby8XJ999pneeOMNbd68+YIPdXvooYf09ttv67bbbtPdd9+tLl26qKioSJ9++qn+9re/6auvvlKzZs2UkJCgRYsWqX///ho1apRyc3OVmpqqNm3a6N///rd9e3PnztX27duVkJCgiIgI5ebmatmyZWrZsqX9gt2a1tu5c2eNHDlSy5YtU0FBgW644QZlZGToiy++uOy56927t3r37n3RMc2bN1dKSooee+wx9e/fX3fccYeOHDmiZcuWqVu3blUu2r3++uvVpk0bPfLIIyopKanRGZGazkFN5vNirrnmGsXHx2vSpEny9va2/4fjscceqzJ23LhxuvPOOyVJ8+bN+9ltX8igQYM0aNCgi4659tprlZiYqJUrVyo/P1+9e/fW7t279eKLL2rw4MG65ZZbLnm/nTt3lru7uxYsWKCCggJ5e3urT58+CgoKutxDgTM58U4w/Er9+Nbzn6p8VsZPn6FRXFxsxo8fb/z9/U3jxo3N8OHDTW5u7gVvPf/prbXVPfvEmKq3sFbe+vraa6+ZlJQUExQUZBo0aGASEhLM119/XWX9//3f/zVDhgwxgYGBxtvb20RERJjhw4ebjIyMn63pYr788ktz5513miZNmhgfHx/TvXt3h+fPVNIl3np+obFz5sxxuM22tLTULFiwwHTo0MF4e3ubpk2bmi5dupjHHnvMFBQU2Nf76a3nxvxwm3xKSopp06aN8fLyMs2aNTM33HCDefrpp+3PlDHGmFWrVpm2bdsab29v0759e5OWlmafq0oZGRlm0KBBJjQ01Hh5eZnQ0FAzcuTIKre217Te77//3kyaNMkEBgYaX19fc/vtt5vjx49f8q3nF3Oh77WlS5ea9u3bG09PTxMcHGwmTJhgvvvuu2q38cgjjxhJpk2bNtX2//TW85rOQU3nszqV3z+vvPKK/et23XXXVXtrtjHGlJSUmKZNmxp/f3/z/fff/+z2jXG89fxiqnvOzvnz581jjz1moqKijKenpwkLCzMpKSnm3LlzDuMiIiJMQkJCtdv86Zy+8MILplWrVsbd3d3h5+NStgHXYDOGq6kAALWrrKxMoaGhuv3227Vq1Spnl4NfOa7ZAQDUuvXr1+vbb7/VuHHjnF0KIM7sAABqza5du/Tvf/9b8+bNU7NmzRwuaAachTM7AIBas3z5ck2YMEFBQUF8MCZcBmd2AACApXFmBwAAWBphBwAAWBoPFdQPnytz8uRJNW7cmEeEAwBQTxhjdObMGYWGhl70gauEHUknT56ssw8LBAAAdev48eNq2bLlBfsJO5IaN24s6YfJ8vPzc3I1AACgJgoLCxUWFmb/O34hhB3936fb+vn5EXYAAKhnfu4SFC5QBgAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlubh7AIAAEDtycrKUl5enrPLcNCsWTOFh4c7bf+EHQAALCIrK0vR0e1UXHzO2aU4aNjQR4cPH3Fa4CHsAABgEXl5eSouPqdXpkcrOryhs8uRJB3OKtaYpw4rLy+PsAMAAGpHdHhDXd+2sbPLcBlcoAwAACyNsAMAACyNsAMAACyNsAMAACyNsAMAACyNsAMAACyNsAMAACyNsAMAACyNsAMAACyNsAMAACyNsAMAACyNsAMAACyNsAMAACyNsAMAACzNqWEnMjJSNputypKUlCRJOnfunJKSkhQYGKhGjRpp6NChysnJcdhGVlaWEhIS1LBhQwUFBemhhx5SWVmZMw4HAAC4IKeGnT179ujUqVP2JT09XZI0bNgwSdKUKVP0zjvvaN26ddq2bZtOnjypIUOG2NcvLy9XQkKCSktLtWPHDr344otavXq1Hn30UaccDwAAcD1ODTvNmzdXSEiIfdmwYYNat26t3r17q6CgQKtWrdKiRYvUp08fdenSRWlpadqxY4d27twpSXrvvfd06NAhvfLKK+rcubMGDBigefPmKTU1VaWlpc48NAAA4CJc5pqd0tJSvfLKK7r33ntls9m0d+9enT9/XnFxcfYx7du3V3h4uDIzMyVJmZmZ6tixo4KDg+1j4uPjVVhYqIMHD15wXyUlJSosLHRYAACANblM2Fm/fr3y8/N19913S5Kys7Pl5eWlJk2aOIwLDg5Wdna2fcyPg05lf2XfhcyfP1/+/v72JSwsrPYOBAAAuBSXCTurVq3SgAEDFBoaWuf7SklJUUFBgX05fvx4ne8TAAA4h4ezC5Ckr7/+Wlu2bNE//vEPe1tISIhKS0uVn5/vcHYnJydHISEh9jG7d+922Fbl3VqVY6rj7e0tb2/vWjwCAADgqlzizE5aWpqCgoKUkJBgb+vSpYs8PT2VkZFhbzty5IiysrIUGxsrSYqNjdWnn36q3Nxc+5j09HT5+fkpJibmyh0AAABwWU4/s1NRUaG0tDQlJibKw+P/yvH399f48eM1depUBQQEyM/PTxMnTlRsbKx69uwpSerXr59iYmI0duxYLVy4UNnZ2Zo5c6aSkpI4cwMAACS5QNjZsmWLsrKydO+991bpW7x4sdzc3DR06FCVlJQoPj5ey5Yts/e7u7trw4YNmjBhgmJjY+Xr66vExETNnTv3Sh4CAABwYU4PO/369ZMxpto+Hx8fpaamKjU19YLrR0REaOPGjXVVHgAAqOdc4podAACAukLYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlub0sHPixAmNGTNGgYGBatCggTp27KiPP/7Y3m+M0aOPPqoWLVqoQYMGiouL09GjRx22cfr0aY0ePVp+fn5q0qSJxo8fr7Nnz17pQwEAAC7IqWHnu+++U69eveTp6al//vOfOnTokJ555hk1bdrUPmbhwoVasmSJVqxYoV27dsnX11fx8fE6d+6cfczo0aN18OBBpaena8OGDdq+fbseeOABZxwSAABwMR7O3PmCBQsUFhamtLQ0e1tUVJT938YYPfvss5o5c6YGDRokSXrppZcUHBys9evXa8SIETp8+LA2bdqkPXv2qGvXrpKk559/XgMHDtTTTz+t0NDQK3tQAADApTj1zM7bb7+trl27atiwYQoKCtJ1112nF154wd5/7NgxZWdnKy4uzt7m7++vHj16KDMzU5KUmZmpJk2a2IOOJMXFxcnNzU27du2qdr8lJSUqLCx0WAAAgDU5Nez85z//0fLly9W2bVtt3rxZEyZM0KRJk/Tiiy9KkrKzsyVJwcHBDusFBwfb+7KzsxUUFOTQ7+HhoYCAAPuYn5o/f778/f3tS1hYWG0fGgAAcBFODTsVFRW6/vrr9eSTT+q6667TAw88oPvvv18rVqyo0/2mpKSooKDAvhw/frxO9wcAAJzHqWGnRYsWiomJcWiLjo5WVlaWJCkkJESSlJOT4zAmJyfH3hcSEqLc3FyH/rKyMp0+fdo+5qe8vb3l5+fnsAAAAGtyatjp1auXjhw54tD2+eefKyIiQtIPFyuHhIQoIyPD3l9YWKhdu3YpNjZWkhQbG6v8/Hzt3bvXPub9999XRUWFevTocQWOAgAAuDKn3o01ZcoU3XDDDXryySc1fPhw7d69WytXrtTKlSslSTabTZMnT9bjjz+utm3bKioqSrNmzVJoaKgGDx4s6YczQf3797e//XX+/HklJydrxIgR3IkFAACcG3a6deumN998UykpKZo7d66ioqL07LPPavTo0fYxDz/8sIqKivTAAw8oPz9fN954ozZt2iQfHx/7mFdffVXJycnq27ev3NzcNHToUC1ZssQZhwQAAFyMU8OOJN1222267bbbLthvs9k0d+5czZ0794JjAgICtGbNmrooDwAA1HNO/7gIAACAukTYAQAAlkbYAQAAlkbYAQAAlkbYAQAAlub0u7EAALiYrKws5eXlObuMKpo1a6bw8HBnl4EaIOwAAFxWVlaWoqPbqbj4nLNLqaJhQx8dPnyEwFMPEHYAAC4rLy9PxcXn9Mr0aEWHN3R2OXaHs4o15qnDysvLI+zUA4QdAIDLiw5vqOvbNnZ2GainuEAZAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYGmEHAABYmlPDzpw5c2Sz2RyW9u3b2/vPnTunpKQkBQYGqlGjRho6dKhycnIctpGVlaWEhAQ1bNhQQUFBeuihh1RWVnalDwUAALgoD2cX0KFDB23ZssX+2sPj/0qaMmWK3n33Xa1bt07+/v5KTk7WkCFD9NFHH0mSysvLlZCQoJCQEO3YsUOnTp3SuHHj5OnpqSeffPKKHwsAAHA9Tg87Hh4eCgkJqdJeUFCgVatWac2aNerTp48kKS0tTdHR0dq5c6d69uyp9957T4cOHdKWLVsUHByszp07a968eZo2bZrmzJkjLy+vK304AADAxTj9mp2jR48qNDRUrVq10ujRo5WVlSVJ2rt3r86fP6+4uDj72Pbt2ys8PFyZmZmSpMzMTHXs2FHBwcH2MfHx8SosLNTBgwcvuM+SkhIVFhY6LAAAwJqcGnZ69Oih1atXa9OmTVq+fLmOHTumm266SWfOnFF2dra8vLzUpEkTh3WCg4OVnZ0tScrOznYIOpX9lX0XMn/+fPn7+9uXsLCw2j0wAADgMpz6NtaAAQPs/+7UqZN69OihiIgIvfHGG2rQoEGd7TclJUVTp061vy4sLCTwALiisrKylJeX5+wyqmjWrJnCw8OdXQZQq5x+zc6PNWnSRFdffbW++OIL3XrrrSotLVV+fr7D2Z2cnBz7NT4hISHavXu3wzYq79aq7jqgSt7e3vL29q79AwCAGsjKylJ0dDsVF59zdilVNGzoo8OHjxB4YCkuFXbOnj2rL7/8UmPHjlWXLl3k6empjIwMDR06VJJ05MgRZWVlKTY2VpIUGxurJ554Qrm5uQoKCpIkpaeny8/PTzExMU47DgC4mLy8PBUXn9Mr06MVHd7Q2eXYHc4q1pinDuvDDz9UdHS0s8uRJB0+fNjZJcACnBp2/vjHP+r2229XRESETp48qdmzZ8vd3V0jR46Uv7+/xo8fr6lTpyogIEB+fn6aOHGiYmNj1bNnT0lSv379FBMTo7Fjx2rhwoXKzs7WzJkzlZSUxJkbAC4vOryhrm/b2Nll2J06XSo3mzRmzBhnl1JFSWmps0tAPebUsPPNN99o5MiR+u9//6vmzZvrxhtv1M6dO9W8eXNJ0uLFi+Xm5qahQ4eqpKRE8fHxWrZsmX19d3d3bdiwQRMmTFBsbKx8fX2VmJiouXPnOuuQAKDeyj9bpgojvTA5UtdfHejsciRJG3f/V7NWf8XDYvGLODXsrF279qL9Pj4+Sk1NVWpq6gXHREREaOPGjbVdGgD8arVr2cBlzjgdzip2dgkX5Wpvs7laPa7Cpa7ZAQCgPnDlt/wk3vb7KcIOAACXyBXf8pN42+9CCDsAag3PjsGvjSu95Se5/tt+zkLYAVAreHYMAFdF2AFQK1z92TF5eXmEHeBXirADoFa52rNjAMDpn3oOAABQlzizA5fBxa0AgLpA2IFL4OJWAEBdIezAJXBxKwCgrhB24FK4uBUAUNu4QBkAAFgaYQcAAFgaYQcAAFga1+wANXD48GFnl1AFt8QDQM0QdoCLOHW6VG42acyYMc4upQpuiQeAmiHsABeRf7ZMFUZ6YXKkrr860Nnl2HFLPADUHGEHqIF2LRtwSzwA1FNcoAwAACyNsAMAACyNsAMAACyNa3YA/Cq40uMDXKkW4NeAsAPA0lz58QElpaXOLgH4VSDsALA0V3x8wMbd/9Ws1V+prKzM2aUAvwqEHQC/Cq70+IDDWcXOLgH4VeECZQAAYGmEHQAAYGmXFXZatWql//73v1Xa8/Pz1apVq19cFAAAQG25rLDz1Vdfqby8vEp7SUmJTpw48YuLAgAAqC2XdIHy22+/bf/35s2b5e/vb39dXl6ujIwMRUZG1lpxAAAAv9QlhZ3BgwdLkmw2mxITEx36PD09FRkZqWeeeabWigMAAPilLinsVFRUSJKioqK0Z88eNWvWrE6KAgAAqC2X9ZydY8eO1XYdAAAAdeKyHyqYkZGhjIwM5ebm2s/4VPrrX//6iwsDAACoDZcVdh577DHNnTtXXbt2VYsWLWSz2Wq7LgAAgFpxWWFnxYoVWr16tcaOHVvb9QAAANSqywo7paWluuGGG2q1kKeeekopKSl68MEH9eyzz0qSzp07pz/84Q9au3atSkpKFB8fr2XLlik4ONi+XlZWliZMmKCtW7eqUaNGSkxM1Pz58+Xhwcd+wfoOHz7s7BLsXKkWAPixy0oE9913n9asWaNZs2bVShF79uzRn//8Z3Xq1MmhfcqUKXr33Xe1bt06+fv7Kzk5WUOGDNFHH30k6Ydn+yQkJCgkJEQ7duzQqVOnNG7cOHl6eurJJ5+sldoAV3TqdKncbNKYMWOcXUoVJaWlzi4BABxcVtg5d+6cVq5cqS1btqhTp07y9PR06F+0aFGNt3X27FmNHj1aL7zwgh5//HF7e0FBgVatWqU1a9aoT58+kqS0tDRFR0dr586d6tmzp9577z0dOnRIW7ZsUXBwsDp37qx58+Zp2rRpmjNnjry8vC7n8ACXl3+2TBVGemFypK6/OtDZ5UiSNu7+r2at/kplZWXOLgUAHFxW2Pn3v/+tzp07S5IOHDjg0HepFysnJSUpISFBcXFxDmFn7969On/+vOLi4uxt7du3V3h4uDIzM9WzZ09lZmaqY8eODm9rxcfHa8KECTp48KCuu+66yzg6oP5o17KBrm/b2NllSJIOZxU7uwQAqNZlhZ2tW7fWys7Xrl2rffv2ac+ePVX6srOz5eXlpSZNmji0BwcHKzs72z7mx0Gnsr+y70JKSkpUUlJif11YWHi5hwAAAFzcZX0QaG04fvy4HnzwQb366qvy8fG5ovueP3++/P397UtYWNgV3T8AALhyLuvMzi233HLRt6vef//9n93G3r17lZubq+uvv97eVl5eru3bt2vp0qXavHmzSktLlZ+f73B2JycnRyEhIZKkkJAQ7d6922G7OTk59r4LSUlJ0dSpU+2vCwsLCTwAAFjUZYWdyut1Kp0/f1779+/XgQMHqnxA6IX07dtXn376qUPbPffco/bt22vatGkKCwuTp6enMjIyNHToUEnSkSNHlJWVpdjYWElSbGysnnjiCeXm5iooKEiSlJ6eLj8/P8XExFxw397e3vL29q7p4QIAgHrsssLO4sWLq22fM2eOzp49W6NtNG7cWNdcc41Dm6+vrwIDA+3t48eP19SpUxUQECA/Pz9NnDhRsbGx6tmzpySpX79+iomJ0dixY7Vw4UJlZ2dr5syZSkpKIsz8jKysLOXl5Tm7DDue0QIAqCu1+uS9MWPGqHv37nr66adrZXuLFy+Wm5ubhg4d6vBQwUru7u7asGGDJkyYoNjYWPn6+ioxMVFz586tlf1bVVZWlqKj26m4+JyzS6mCZ7QAAGpbrYadzMzMX3Sx8QcffODw2sfHR6mpqUpNTb3gOhEREdq4ceNl7/PXKC8vT8XF5/TK9GhFhzd0djmSeEYLAKDuXFbYGTJkiMNrY4xOnTqljz/+uNaeqoy6Fx3ekGe0AAAs77LCjr+/v8NrNzc3tWvXTnPnzlW/fv1qpTAAAIDacFlhJy0trbbrAAAAqBO/6JqdvXv32u+i6dChAx/PAAAAXM5lhZ3c3FyNGDFCH3zwgf2Bf/n5+brlllu0du1aNW/evDZrBAAAuGyX9XEREydO1JkzZ3Tw4EGdPn1ap0+f1oEDB1RYWKhJkybVdo0AAACX7bLO7GzatElbtmxRdHS0vS0mJkapqalcoAwAAFzKZZ3ZqaiokKenZ5V2T09PVVRU/OKiAAAAastlhZ0+ffrowQcf1MmTJ+1tJ06c0JQpU9S3b99aKw4AAOCXuqyws3TpUhUWFioyMlKtW7dW69atFRUVpcLCQj3//PO1XSMAAMBlu6xrdsLCwrRv3z5t2bJFn332mSQpOjpacXFxtVocAADAL3VJZ3bef/99xcTEqLCwUDabTbfeeqsmTpyoiRMnqlu3burQoYM+/PDDuqoVAADgkl1S2Hn22Wd1//33y8/Pr0qfv7+//ud//keLFi2qteIAAAB+qUsKO5988on69+9/wf5+/fpp7969v7goAACA2nJJYScnJ6faW84reXh46Ntvv/3FRQEAANSWSwo7V111lQ4cOHDB/n//+99q0aLFLy4KAACgtlxS2Bk4cKBmzZqlc+fOVen7/vvvNXv2bN122221VhwAAMAvdUm3ns+cOVP/+Mc/dPXVVys5OVnt2rWTJH322WdKTU1VeXm5HnnkkTopFAAA4HJcUtgJDg7Wjh07NGHCBKWkpMgYI0my2WyKj49XamqqgoOD66TQ+iorK0t5eXnOLsPB4cOHnV0CAABXzCU/VDAiIkIbN27Ud999py+++ELGGLVt21ZNmzati/rqtaysLEVHt1NxcdW3/VxBSWmps0sAAKDOXdYTlCWpadOm6tatW23WYjl5eXkqLj6nV6ZHKzq8obPLsdu4+7+atforlZWVObsUAADq3GWHHdRcdHhDXd+2sbPLsDucVezsEgAAuGIu64NAAQAA6gvCDgAAsDTCDgAAsDTCDgAAsDTCDgAAsDTCDgAAsDTCDgAAsDTCDgAAsDTCDgAAsDTCDgAAsDTCDgAAsDTCDgAAsDTCDgAAsDTCDgAAsDTCDgAAsDSnhp3ly5erU6dO8vPzk5+fn2JjY/XPf/7T3n/u3DklJSUpMDBQjRo10tChQ5WTk+OwjaysLCUkJKhhw4YKCgrSQw89pLKysit9KAAAwEU5Ney0bNlSTz31lPbu3auPP/5Yffr00aBBg3Tw4EFJ0pQpU/TOO+9o3bp12rZtm06ePKkhQ4bY1y8vL1dCQoJKS0u1Y8cOvfjii1q9erUeffRRZx0SAABwMR7O3Pntt9/u8PqJJ57Q8uXLtXPnTrVs2VKrVq3SmjVr1KdPH0lSWlqaoqOjtXPnTvXs2VPvvfeeDh06pC1btig4OFidO3fWvHnzNG3aNM2ZM0deXl7OOCwAAOBCXOaanfLycq1du1ZFRUWKjY3V3r17df78ecXFxdnHtG/fXuHh4crMzJQkZWZmqmPHjgoODraPiY+PV2Fhof3sUHVKSkpUWFjosAAAAGtyetj59NNP1ahRI3l7e+t3v/ud3nzzTcXExCg7O1teXl5q0qSJw/jg4GBlZ2dLkrKzsx2CTmV/Zd+FzJ8/X/7+/vYlLCysdg8KAAC4DKeHnXbt2mn//v3atWuXJkyYoMTERB06dKhO95mSkqKCggL7cvz48TrdHwAAcB6nXrMjSV5eXmrTpo0kqUuXLtqzZ4+ee+453XXXXSotLVV+fr7D2Z2cnByFhIRIkkJCQrR7926H7VXerVU5pjre3t7y9vau5SMBAACuyOlndn6qoqJCJSUl6tKlizw9PZWRkWHvO3LkiLKyshQbGytJio2N1aeffqrc3Fz7mPT0dPn5+SkmJuaK1w4AAFyPU8/spKSkaMCAAQoPD9eZM2e0Zs0affDBB9q8ebP8/f01fvx4TZ06VQEBAfLz89PEiRMVGxurnj17SpL69eunmJgYjR07VgsXLlR2drZmzpyppKQkztwAAABJTg47ubm5GjdunE6dOiV/f3916tRJmzdv1q233ipJWrx4sdzc3DR06FCVlJQoPj5ey5Yts6/v7u6uDRs2aMKECYqNjZWvr68SExM1d+5cZx0SAABwMU4NO6tWrbpov4+Pj1JTU5WamnrBMREREdq4cWNtlwYAACzC5a7ZAQAAqE2EHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGmEHQAAYGlODTvz589Xt27d1LhxYwUFBWnw4ME6cuSIw5hz584pKSlJgYGBatSokYYOHaqcnByHMVlZWUpISFDDhg0VFBSkhx56SGVlZVfyUAAAgItyatjZtm2bkpKStHPnTqWnp+v8+fPq16+fioqK7GOmTJmid955R+vWrdO2bdt08uRJDRkyxN5fXl6uhIQElZaWaseOHXrxxRe1evVqPfroo844JAAA4GI8nLnzTZs2ObxevXq1goKCtHfvXv3mN79RQUGBVq1apTVr1qhPnz6SpLS0NEVHR2vnzp3q2bOn3nvvPR06dEhbtmxRcHCwOnfurHnz5mnatGmaM2eOvLy8nHFoAADARbjUNTsFBQWSpICAAEnS3r17df78ecXFxdnHtG/fXuHh4crMzJQkZWZmqmPHjgoODraPiY+PV2FhoQ4ePFjtfkpKSlRYWOiwAAAAa3KZsFNRUaHJkyerV69euuaaayRJ2dnZ8vLyUpMmTRzGBgcHKzs72z7mx0Gnsr+yrzrz58+Xv7+/fQkLC6vlowEAAK7CZcJOUlKSDhw4oLVr19b5vlJSUlRQUGBfjh8/Xuf7BAAAzuHUa3YqJScna8OGDdq+fbtatmxpbw8JCVFpaany8/Mdzu7k5OQoJCTEPmb37t0O26u8W6tyzE95e3vL29u7lo8CAAC4Iqee2THGKDk5WW+++abef/99RUVFOfR36dJFnp6eysjIsLcdOXJEWVlZio2NlSTFxsbq008/VW5urn1Menq6/Pz8FBMTc2UOBAAAuCynntlJSkrSmjVr9NZbb6lx48b2a2z8/f3VoEED+fv7a/z48Zo6daoCAgLk5+eniRMnKjY2Vj179pQk9evXTzExMRo7dqwWLlyo7OxszZw5U0lJSZy9AQAAzg07y5cvlyTdfPPNDu1paWm6++67JUmLFy+Wm5ubhg4dqpKSEsXHx2vZsmX2se7u7tqwYYMmTJig2NhY+fr6KjExUXPnzr1ShwEAAFyYU8OOMeZnx/j4+Cg1NVWpqakXHBMREaGNGzfWZmkAAMAiXOZuLAAAgLpA2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJZG2AEAAJbm1LCzfft23X777QoNDZXNZtP69esd+o0xevTRR9WiRQs1aNBAcXFxOnr0qMOY06dPa/To0fLz81OTJk00fvx4nT179goeBQAAcGVODTtFRUW69tprlZqaWm3/woULtWTJEq1YsUK7du2Sr6+v4uPjde7cOfuY0aNH6+DBg0pPT9eGDRu0fft2PfDAA1fqEAAAgIvzcObOBwwYoAEDBlTbZ4zRs88+q5kzZ2rQoEGSpJdeeknBwcFav369RowYocOHD2vTpk3as2ePunbtKkl6/vnnNXDgQD399NMKDQ29YscCAABck8tes3Ps2DFlZ2crLi7O3ubv768ePXooMzNTkpSZmakmTZrYg44kxcXFyc3NTbt27brgtktKSlRYWOiwAAAAa3LZsJOdnS1JCg4OdmgPDg6292VnZysoKMih38PDQwEBAfYx1Zk/f778/f3tS1hYWC1XDwAAXIXLhp26lJKSooKCAvty/PhxZ5cEAADqiMuGnZCQEElSTk6OQ3tOTo69LyQkRLm5uQ79ZWVlOn36tH1Mdby9veXn5+ewAAAAa3LZsBMVFaWQkBBlZGTY2woLC7Vr1y7FxsZKkmJjY5Wfn6+9e/fax7z//vuqqKhQjx49rnjNAADA9Tj1bqyzZ8/qiy++sL8+duyY9u/fr4CAAIWHh2vy5Ml6/PHH1bZtW0VFRWnWrFkKDQ3V4MGDJUnR0dHq37+/7r//fq1YsULnz59XcnKyRowYwZ1YAABAkpPDzscff6xbbrnF/nrq1KmSpMTERK1evVoPP/ywioqK9MADDyg/P1833nijNm3aJB8fH/s6r776qpKTk9W3b1+5ublp6NChWrJkyRU/FgAA4JqcGnZuvvlmGWMu2G+z2TR37lzNnTv3gmMCAgK0Zs2auigPAABYgMteswMAAFAbCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSLBN2UlNTFRkZKR8fH/Xo0UO7d+92dkkAAMAFWCLsvP7665o6dapmz56tffv26dprr1V8fLxyc3OdXRoAAHAyS4SdRYsW6f7779c999yjmJgYrVixQg0bNtRf//pXZ5cGAACcrN6HndLSUu3du1dxcXH2Njc3N8XFxSkzM9OJlQEAAFfg4ewCfqm8vDyVl5crODjYoT04OFifffZZteuUlJSopKTE/rqgoECSVFhYWKu1nT17VpK09+gZnf2+vFa3/UscziqSJO3/skjGlu/cYv4/V6xJoq5L4Yo1Sa5ZlyvWJLlmXa5Yk0Rdl+LIN8WSfvibWNt/Zyu3Z4y5+EBTz504ccJIMjt27HBof+ihh0z37t2rXWf27NlGEgsLCwsLC4sFluPHj180K9T7MzvNmjWTu7u7cnJyHNpzcnIUEhJS7TopKSmaOnWq/XVFRYVOnz6twMBA2Wy2Oq3X1RQWFiosLEzHjx+Xn5+fs8upt5jH2sE81g7msXYwj7WjLufRGKMzZ84oNDT0ouPqfdjx8vJSly5dlJGRocGDB0v6IbxkZGQoOTm52nW8vb3l7e3t0NakSZM6rtS1+fn58cNcC5jH2sE81g7msXYwj7WjrubR39//Z8fU+7AjSVOnTlViYqK6du2q7t2769lnn1VRUZHuueceZ5cGAACczBJh56677tK3336rRx99VNnZ2ercubM2bdpU5aJlAADw62OJsCNJycnJF3zbChfm7e2t2bNnV3lbD5eGeawdzGPtYB5rB/NYO1xhHm3G/Nz9WgAAAPVXvX+oIAAAwMUQdgAAgKURdgAAgKURdgAAgKURdn6l5s+fr27duqlx48YKCgrS4MGDdeTIEWeXVa899dRTstlsmjx5srNLqZdOnDihMWPGKDAwUA0aNFDHjh318ccfO7useqW8vFyzZs1SVFSUGjRooNatW2vevHk//7lBv3Lbt2/X7bffrtDQUNlsNq1fv96h3xijRx99VC1atFCDBg0UFxeno0ePOqdYF3axeTx//rymTZumjh07ytfXV6GhoRo3bpxOnjx5RWoj7PxKbdu2TUlJSdq5c6fS09N1/vx59evXT0VFRc4urV7as2eP/vznP6tTp07OLqVe+u6779SrVy95enrqn//8pw4dOqRnnnlGTZs2dXZp9cqCBQu0fPlyLV26VIcPH9aCBQu0cOFCPf/8884uzaUVFRXp2muvVWpqarX9Cxcu1JIlS7RixQrt2rVLvr6+io+P17lz565wpa7tYvNYXFysffv2adasWdq3b5/+8Y9/6MiRI7rjjjuuTHG18WGcqP9yc3ONJLNt2zZnl1LvnDlzxrRt29akp6eb3r17mwcffNDZJdU706ZNMzfeeKOzy6j3EhISzL333uvQNmTIEDN69GgnVVT/SDJvvvmm/XVFRYUJCQkxf/rTn+xt+fn5xtvb27z22mtOqLB++Ok8Vmf37t1Gkvn666/rvB7O7ECSVFBQIEkKCAhwciX1T1JSkhISEhQXF+fsUuqtt99+W127dtWwYcMUFBSk6667Ti+88IKzy6p3brjhBmVkZOjzzz+XJH3yySf617/+pQEDBji5svrr2LFjys7Odvj59vf3V48ePZSZmenEyuq/goIC2Wy2K/LZlJZ5gjIuX0VFhSZPnqxevXrpmmuucXY59cratWu1b98+7dmzx9ml1Gv/+c9/tHz5ck2dOlUzZszQnj17NGnSJHl5eSkxMdHZ5dUb06dPV2Fhodq3by93d3eVl5friSee0OjRo51dWr2VnZ0tSVU+fig4ONjeh0t37tw5TZs2TSNHjrwiH7JK2IGSkpJ04MAB/etf/3J2KfXK8ePH9eCDDyo9PV0+Pj7OLqdeq6ioUNeuXfXkk09Kkq677jodOHBAK1asIOxcgjfeeEOvvvqq1qxZow4dOmj//v2aPHmyQkNDmUe4jPPnz2v48OEyxmj58uVXZJ+8jfUrl5ycrA0bNmjr1q1q2bKls8upV/bu3avc3Fxdf/318vDwkIeHh7Zt26YlS5bIw8ND5eXlzi6x3mjRooViYmIc2qKjo5WVleWkiuqnhx56SNOnT9eIESPUsWNHjR07VlOmTNH8+fOdXVq9FRISIknKyclxaM/JybH3oeYqg87XX3+t9PT0K3JWRyLs/GoZY5ScnKw333xT77//vqKiopxdUr3Tt29fffrpp9q/f7996dq1q0aPHq39+/fL3d3d2SXWG7169ary6IPPP/9cERERTqqofiouLpabm+OvdXd3d1VUVDipovovKipKISEhysjIsLcVFhZq165dio2NdWJl9U9l0Dl69Ki2bNmiwMDAK7Zv3sb6lUpKStKaNWv01ltvqXHjxvb3nv39/dWgQQMnV1c/NG7cuMo1Tr6+vgoMDOTap0s0ZcoU3XDDDXryySc1fPhw7d69WytXrtTKlSudXVq9cvvtt+uJJ55QeHi4OnTooP/93//VokWLdO+99zq7NJd29uxZffHFF/bXx44d0/79+xUQEKDw8HBNnjxZjz/+uNq2bauoqCjNmjVLoaGhGjx4sPOKdkEXm8cWLVrozjvv1L59+7RhwwaVl5fb/+4EBATIy8urbour8/u94JIkVbukpaU5u7R6jVvPL98777xjrrnmGuPt7W3at29vVq5c6eyS6p3CwkLz4IMPmvDwcOPj42NatWplHnnkEVNSUuLs0lza1q1bq/19mJiYaIz54fbzWbNmmeDgYOPt7W369u1rjhw54tyiXdDF5vHYsWMX/LuzdevWOq/NZgyP1gQAANbFNTsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAAMDSCDsAUI05c+aoc+fOzi4DQC0g7AD41bPZbFq/fr2zywBQRwg7AADA0gg7AFzGzTffrIkTJ2ry5Mlq2rSpgoOD9cILL6ioqEj33HOPGjdurDZt2uif//ynfZ1t27ape/fu8vb2VosWLTR9+nSVlZU5bHPSpEl6+OGHFRAQoJCQEM2ZM8feHxkZKUn67W9/K5vNZn9d6eWXX1ZkZKT8/f01YsQInTlzpi6nAEAdIOwAcCkvvviimjVrpt27d2vixImaMGGChg0bphtuuEH79u1Tv379NHbsWBUXF+vEiRMaOHCgunXrpk8++UTLly/XqlWr9Pjjj1fZpq+vr3bt2qWFCxdq7ty5Sk9PlyTt2bNHkpSWlqZTp07ZX0vSl19+qfXr12vDhg3asGGDtm3bpqeeeurKTQaAWsEHgQJwGTfffLPKy8v14YcfSpLKy8vl7++vIUOG6KWXXpIkZWdnq0WLFsrMzNQ777yjv//97zp8+LBsNpskadmyZZo2bZoKCgrk5uZWZZuS1L17d/Xp08ceXGw2m958800NHjzYPmbOnDn605/+pOzsbDVu3FiS9PDDD2v79u3auXPnlZgOALWEMzsAXEqnTp3s/3Z3d1dgYKA6duxobwsODpYk5ebm6vDhw4qNjbUHHUnq1auXzp49q2+++ababUpSixYtlJub+7O1REZG2oPOpawHwLUQdgC4FE9PT4fXNpvNoa0y2FRUVPyibdZk/ctdD4BrIewAqLeio6OVmZmpH78b/9FHH6lx48Zq2bJljbfj6emp8vLyuigRgAsg7ACot37/+9/r+PHjmjhxoj777DO99dZbmj17tqZOnSo3t5r/eouMjFRGRoays7P13Xff1WHFAJyBsAOg3rrqqqu0ceNG7d69W9dee61+97vfafz48Zo5c+YlbeeZZ55Renq6wsLCdN1119VRtQCchbuxAACApXFmBwAAWBphBwAAWBphBwAAWBphBwAAWBphBwAAWBphBwAAWBphBwAAWBphBwAAWBphBwAAWBphBwAAWBphBwAAWBphBwAAWNr/A6AixIs39I+UAAAAAElFTkSuQmCC\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "# A Majority of the movie breakeven after production with an estimated net revenue of between 300M-500M US dolars\n",
        "sns.scatterplot(data = movie_budget_clean, x =\"net_gross\",y=\"production_budget\", palette ='terrain').set_title('Correction between Production Budget and Net Revenue')"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 559
        },
        "id": "hDV0aMQ7cQeV",
        "outputId": "dab7dba1-52ec-4f64-e2a8-d1ba9624607d"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "<ipython-input-53-288af8a8debb>:2: UserWarning: Ignoring `palette` because no `hue` variable has been assigned.\n",
            "  sns.scatterplot(data = movie_budget_clean, x =\"net_gross\",y=\"production_budget\", palette ='terrain').set_title('Correction between Production Budget and Net Revenue')\n"
          ]
        },
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "Text(0.5, 1.0, 'Correction between Production Budget and Net Revenue')"
            ]
          },
          "metadata": {},
          "execution_count": 53
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "iVBORw0KGgoAAAANSUhEUgAAAioAAAHWCAYAAABZiKJMAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjcuMSwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy/bCgiHAAAACXBIWXMAAA9hAAAPYQGoP6dpAADRtElEQVR4nOydd3gUVdvG7+0t2d2QAgRICCQQWiAUKUlooqggItiAT6qISrA3VBRsiJUXUGwgvr6igigoYkNQmlKjdEggJEhP22SzfXe+PzYzbG/ZJJvk+V0XF8nszJkzZzY7z55zP/fDYxiGAUEQBEEQRATCb+gOEARBEARBeIMCFYIgCIIgIhYKVAiCIAiCiFgoUCEIgiAIImKhQIUgCIIgiIiFAhWCIAiCICIWClQIgiAIgohYKFAhCIIgCCJioUCFIAiCIIiIhQKVZsTQoUMxdOjQej/vqlWrwOPxsG/fvno/NxE6DfV+AQAej4f58+c3yLnrk4Yc44bmzJkz4PF4WLVqVUN3hYhwmn2gcurUKcyaNQsdOnSAVCqFUqlEVlYW/vOf/0Cv1zd094Lm6NGjmD9/Ps6cOdPQXalTNm3a1KQfZOyHOPtPIBAgKSkJt956K/7++++G7l5YiMR7OH/+fKdx5/P5aN26NUaPHo2//vqrobsXErt27cL8+fNRUVHR0F0Jid9//527H/v373d7ferUqYiKigqp7WDfg0OHDnV6f8hkMmRkZGDx4sWw2Wwh9YHwj7ChO9CQ/PDDD7j99tshkUgwefJkdO/eHSaTCTt27MATTzyBI0eO4MMPP2zobgbF0aNHsWDBAgwdOhTt27d3eu2XX35pmE7VAZs2bcK7774bcQ+6cDNhwgTcdNNNsFqtOHbsGJYvX44ff/wRf/31F3r16tXQ3asVvu6hXq+HUNhwH0/Lly9HVFQUbDYbzp49i48++giDBw/Gnj17Gt2479q1CwsWLMDUqVOhVqsbuju1Yv78+fj+++/D1l4onyNt27bFwoULAQAlJSVYvXo1HnnkEVy5cgWvvPJK2PpGXKXZBiqFhYW46667kJycjC1btqB169bca7Nnz0ZBQQF++OGHWp+HYRgYDAbIZDK31wwGA8RiMfj8+pnYEovF9XIeInz07t0b//d//8f9npWVhTFjxmD58uX44IMPPB5TXV0NhUJRX12sE6RSaYOe/7bbbkNcXBz3+9ixY9G9e3esXbu20QUqTYVevXph48aNOHDgAHr37t1g/VCpVE5/k/fddx/S09OxdOlSvPjiixAIBA3Wt6ZKs136ef3116HVarFixQqnIIUlNTUVDz30EPe7xWLBSy+9hI4dO0IikaB9+/Z45plnYDQanY5r3749Ro8ejZ9//hl9+/aFTCbDBx98wE1ffvnll3juuefQpk0byOVyVFZWAgB2796NG264ASqVCnK5HEOGDMHOnTvd+nXu3DnMmDEDiYmJkEgkSElJwf333w+TyYRVq1bh9ttvBwAMGzaMm578/fffAXheD798+TJmzJiBli1bQiqVomfPnvj000+d9mGXId588018+OGH3Bj069cPe/fuDXjMdTodZs2ahdjYWCiVSkyePBnl5eVu+/3444/IycmBQqFAdHQ0Ro0ahSNHjnCvT506Fe+++y4AOE3DAvYH+7hx45za69GjB3g8Hg4ePMht++qrr8Dj8XDs2DGnsZ0+fTpatmwJiUSCbt26YeXKlW79MxqNeOGFF5CamgqJRIJ27drhySefdHsv8Hg85ObmYv369ejevTvX5k8//RTwmLkyfPhwAPZAG7iq//njjz/wwAMPICEhAW3btuX2f++999CtWzdIJBIkJiZi9uzZHpcA2Psqk8lwzTXXYPv27W77sOdyXVZk39vs+4xl9+7duOmmmxATEwOFQoGMjAz85z//AeD7HrLbXL/l5uXl4cYbb4RSqURUVBSuvfZat+UYto87d+7Eo48+ivj4eCgUCtx66624cuWK94H1Q6tWrQDAaZYn2PEIZIwBoKioCGPGjIFCoUBCQgIeeeQR/Pzzz17H2Nfnxvz58/HEE08AAFJSUrhx9rU0vH37dtx+++1ISkri3t+PPPKI21I4u+Ry7tw5jB07FlFRUYiPj8fjjz8Oq9XqtG9FRQWmTp0KlUoFtVqNKVOmBL0UNWfOHMTExAQ8+1Gbz5FgkEql6NevH6qqqnD58mWn1/73v/+hT58+kMlkaNGiBe666y6cPXuWez03NxdRUVHQ6XRu7U6YMAGtWrVyGkt/18ReVyD3xdv71Jt26Pjx47jtttvQokULSKVS9O3bF999912wwxUSzXZG5fvvv0eHDh0waNCggPa/55578Omnn+K2227DY489ht27d2PhwoU4duwYvv32W6d9T5w4gQkTJmDW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4u677xaZmZmioqJC+Hw+cffdd4shQ4Y02um2MSKRiBg4cKA4++yzxbp168SyZcvEmDFjBCAWLFgghBBi586dAhB9+vQR8+fPFzt27BD79u0TTzzxhHC73eLVV18VmzZtEvfee6+wWq1iy5YtQgghHn/8cZGXlyc+/fRT8f3334tly5aJV155RQghxBtvvCHcbrd4//33xa5du8Tnn38u/v73v3fcwkokxxh1/w0KIcSuXbuEpmli7969CePOOusscd999wkhhHjuueeEy+USS5YsEbqui82bN4tBgwYJQHz22Wetv3a7vAOJRHJcMmHCBFFSUpJwbPTo0eLXv/61WLZsmXC73SIQCCSc79evn3juueeEEELMnDlTjBgxotXXW7hwobBYLGL//v3xY4sXL240UHnqqacSnpubmyt+97vfNZjrLbfcIoQQ4rbbbhMTJ04UhmE0uO6f/vQnMWDAABEKhVo9V4nkRKJ+oPLuu+8KQCQlJSX8WCwWcdlllwkhhDAMQ9x7773C4XAITdNEenq6mDVrlgDEqlWrWn1tSztkfyQSyXHM8OHDEx736NGDAwcO8PXXX+PxeMjMzEw47/f72b59+xFda/PmzeTl5ZGTkxM/NmbMmEbHnnLKKfG/19TUsG/fPsaNG5cwZty4cfGtqGuuuYazzz6bgQMHMnnyZC688ELOOeccAC699FKeeuopCgoKmDx5Mueffz5TpkzBYpEfkRJJY3g8HjRNY/Xq1WialnAuOTkZAEVRePTRR/n9739PaWkp3bp148MPPwSgoKCg1deS/wolEkmzWK3WhMeKomAYBh6Phx49eiSI52KkpaV1+LySkpLaNH7UqFHs3LmThQsXsmTJEi677DImTZrEm2++SV5eHps3b2bJkiUsXryYW265hccff5ylS5c2eP8SiQSKiorQdZ0DBw4wfvz4ZsdqmkbPnj0BePXVVxk7dizdunVr9bVkoCKRSI6IUaNGUVpaisVioU+fPo2Osdls6Lre6tccOHAgP/zwA2VlZWRnZwPw5Zdftvg8t9tNbm4uK1asYMKECfHjK1asSMjIuN1uLr/8ci6//HJ++tOfMnnyZA4dOkRGRgZOp5MpU6YwZcoUbr31VgYNGsT69esZNWpUq+cvkRxPeDwetm3bFn+8c+dO1q1bR0ZGBgMGDOCqq67i5z//OX/6058oKiri4MGDfPjhhwwfPpwLLriA8vJy3nzzTc444wwCgQBz587ljTfeYOnSpW2ahwxUJBLJETFp0iTGjh3L1KlTeeyxxxgwYAD79u3jvffe4+KLL+aUU06hT58+8Q+3Xr16kZKSgt1ub/I1zz77bPr168e0adN47LHHqK2t5Te/+Q1gZnKa45577mHmzJn069ePkSNHMnfuXNatW8fLL78MwBNPPEGPHj0oKipCVVXeeOMNcnJySEtLY968eei6TnFxMS6Xi5deegmn00nv3r3bb8EkkmOMr776ijPPPDP++K677gJg2rRpzJs3j7lz5/Lwww9z9913s3fvXrKysjj11FO58MIL48954YUX+NWvfoUQgrFjx/LJJ580uZ3bJO2st5FIJMcREyZMEHfccUfCsYsuukhMmzZNCCFETU2NuO2220Rubq6wWq0iLy9PXHXVVWL37t1CCCECgYC45JJLRFpamgDE3LlzW7zmxo0bxbhx44TNZhODBg0S77zzjgDEokWLhBCHxbRr165NeJ6u62LWrFmiZ8+ewmq1ihEjRoiFCxfGz//9738XI0eOFElJScLtdouzzjpLrFmzRgghxIIFC0RxcbFwu90iKSlJnHrqqWLJkiVHtmgSiaRdUYRog+uKRCKRHGVWrFhBSUkJ27Zto1+/fp09HYlEcpSRgYpEIulSLFiwgOTkZPr378+2bdu44447SE9PZ/ny5Z09NYlE0glIZ1qJRHLUePnll0lOTm70Z8iQIQDU1tbGxazXXHMNo0eP5u233+7kmUskks5CZlQkEslRo7a2lrKyskbPWa1WKV6VSCQNkIGKRCKRSCSSLovc+pFIJBKJRNJlkYGKRCKRSCSSLosMVCQSiUQikXRZZKAikUgkEomkyyIDFYlEIpFIJF0WGahIJBKJRCLpsshARSKRSCQSSZdFBioSiUQikUi6LP8ffQ5ri2XbsCQAAAAASUVORK5CYII=\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "# A Majority of the movies breakeven after production with an estimated net revenue of between 300M-500M US dollars\n",
        "sns.scatterplot(x='production_budget',y='net_gross',data = movie_budget_clean,color='blue').set_title('Correction between Production Budget and Net Earnings')"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 504
        },
        "id": "QWhNu_qev4NE",
        "outputId": "5a905eb6-b1d5-4b7a-9e32-f5a0e0e72032"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "Text(0.5, 1.0, 'Correction between Production Budget and Net Earnings')"
            ]
          },
          "metadata": {},
          "execution_count": 54
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "iVBORw0KGgoAAAANSUhEUgAAAjcAAAHWCAYAAACL2KgUAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjcuMSwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy/bCgiHAAAACXBIWXMAAA9hAAAPYQGoP6dpAAC5M0lEQVR4nOydd3gU5fr3v5tACimbAAkECUXwCIiAIF0ETQgqRSyAeM4B/UlRQAi2I8oROKKIihQLRRTUcxAFBQVRUmhSpQUQCEgPEGrCJoQUSJ73j/t9dmZnZ1uyyW429+e6ciU7O+WZmc0+37mrQQghwDAMwzAM4yP4eXoADMMwDMMw7oTFDcMwDMMwPgWLG4ZhGIZhfAoWNwzDMAzD+BQsbhiGYRiG8SlY3DAMwzAM41OwuGEYhmEYxqdgccMwDMMwjE/B4oZhGIZhGJ+CxQ1jlx49eqBHjx4VftzFixfDYDBg165dFX5spvR46vMCAAaDAZMnT/bIsSsST15jT3Pq1CkYDAYsXrzY00Op1FSF68jiphQcP34cI0eOxO23346goCCEh4eja9eumD17NvLz8z09PJc5dOgQJk+ejFOnTnl6KOXKmjVrfHryk19Y8sff3x8NGjTAY489hrS0NE8Pzy144z2cPHmyxXX38/NDTEwM+vTpg+3bt3t6eKVi69atmDx5Mq5du+bpoZSKDRs2mO/H7t27rd5/5plnEBoaWqp9u/oZ7NGjh8XnQ/3TrFmzUo2BcUw1Tw+gsvHLL79gwIABCAwMxJAhQ9CyZUsUFRVh8+bNePXVV3Hw4EEsWLDA08N0iUOHDmHKlCno0aMHGjVqZPFeUlKSZwZVDqxZswaffvqp102O7mbw4MF45JFHUFxcjMOHD2Pu3Ln49ddfsX37drRp08bTwysT9u5hfn4+qlXz3Ffa3LlzERoaipKSEmRkZODzzz/H/fffjz/++KPSXfetW7diypQpeOaZZxAREeHp4ZSJyZMnY9WqVW7bX2m+R+rXr49p06ZZLTcajW4blys0bNgQ+fn5qF69ukeOXxGwuHGBkydP4qmnnkLDhg2xbt06xMTEmN8bPXo0jh07hl9++aXMxxFCoKCgAMHBwVbvFRQUICAgAH5+FWN0CwgIqJDjMO6jbdu2+Mc//mF+3bVrV/Tr1w9z587F/PnzdbfJy8tDSEhIRQ2xXAgKCvLo8Z988knUrl3b/Lp///5o2bIlli1bVunEja/Qpk0brF69Gnv27EHbtm09Ng6j0WjxP+luXP3/NRgMHv9/KW/YLeUC77//Pq5fv44vvvjCQthImjZtinHjxplf37p1C2+//TaaNGmCwMBANGrUCG+88QYKCwsttmvUqBH69OmDtWvX4t5770VwcDDmz59vNq0uXboUEydOxG233YYaNWogJycHALBjxw489NBDMBqNqFGjBrp3744tW7ZYjevcuXN47rnnUK9ePQQGBqJx48Z44YUXUFRUhMWLF2PAgAEAgAceeMBsLt2wYQMAff/+pUuX8Nxzz6FOnToICgpC69at8dVXX1msI10kH374IRYsWGC+Bu3bt8fOnTudvuY3btzAyJEjUatWLYSHh2PIkCHIzs62Wu/XX39Ft27dEBISgrCwMPTu3RsHDx40v//MM8/g008/BQALszBAYuDxxx+32N/dd98Ng8GA/fv3m5d99913MBgMOHz4sMW1/b//+z/UqVMHgYGBuOuuu/Dll19aja+wsBCTJk1C06ZNERgYiNjYWLz22mtWnwWDwYAxY8Zg5cqVaNmypXmfv/32m9PXTMuDDz4IgMQ5oMQzbdy4EaNGjUJ0dDTq169vXv+zzz7DXXfdhcDAQNSrVw+jR4/WdU/I+xocHIwOHTrg999/t1pHHkvr8pSfbfk5k+zYsQOPPPIIIiMjERISglatWmH27NkA7N9DuUz7NL137148/PDDCA8PR2hoKOLi4qxcRXKMW7ZswUsvvYSoqCiEhITgsccew+XLl21fWAfUrVsXACysSa5eD2euMQCcPn0a/fr1Q0hICKKjozF+/HisXbvW5jW2970xefJkvPrqqwCAxo0bm6+zPbf177//jgEDBqBBgwbmz/f48eOt3PTSHXTu3Dn0798foaGhiIqKwiuvvILi4mKLda9du4ZnnnkGRqMRERERGDp0qMtushdffBGRkZFOW1nK8j1SVk6fPo1Ro0bhzjvvRHBwMGrVqoUBAwZYXXd7/789evRAy5YtcejQITzwwAOoUaMGbrvtNrz//vsW+9CLuXHl3ly9ehX//Oc/ER4ebr43+/bts9rnhQsX8Oyzz6J+/foIDAxETEwMHn300QoJgWDLjQusWrUKt99+O7p06eLU+sOGDcNXX32FJ598Ei+//DJ27NiBadOm4fDhw1ix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9evXrd6X6at+fn7o378/Vq1apdvGQCp5Ga3vzD/RI488ggsXLlhkkNy6dQsff/wxQkND0b1799Kckk0WLFiAmzdvml/PnTsXt27dMkf99+rVC+Hh4Xj33Xct1pOoU3ntnad0N02fPh2tWrUyxzV069YNqamp2LVrl3kdgJ5wnnjiCfzwww+64lF93IEDB+LcuXP4/PPPrdbLz8+3yHTwJPHx8QgICMCcOXMsnvK++OILmEwm82f23nvvRVRUFObNm4eioiLzeosXL7a6tnLSkPFMAD3pa115bdu2RePGjTFr1iyrfajH4uxn1d/fHwkJCfjpp58s0k4vXryIJUuW4L777iuzq8ERWVlZ2Lp1K+rWrYvo6GgAzl8PV65xr169cO7cOfz888/mZQUFBVafN2e/NwDXvhOk4FffJyGE+buwNDzyyCO4desW5s6da15WXFyMjz/+uNT7lNabn376yapit7u+R8qCv7+/lXXl448/9jorZ69evXDz5k2Lz1dJSYk5RV5y48YNFBQUWCxr0qQJwsLCrEpglAdsuXGBJk2aYMmSJRg0aBCaN29uUaF469at5pRoAGjdujWGDh2KBQsW4Nq1a+jevTv++OMPfPXVV+jfv7+FNcJV/Pz8sHDhQjz88MO466678Oyzz+K2227DuXPnsH79eoSHh5srcr777rtISkpC9+7dzWnImZmZWLZsGTZv3oyIiAi0adMG/v7+mD59OkwmEwIDA/Hggw+av5DVjBgxAvPnz8czzzyD3bt3o1GjRli+fDm2bNmCWbNmOR1w7SxFRUWIi4vDwIEDceTIEXz22We47777zMGT4eHhmDt3Lv75z3+ibdu2eOqppxAVFYUzZ87gl19+QdeuXfHJJ58AoC93ABg7dix69eoFf39/PPXUUwDIX1y3bl0cOXLEImjx/vvvx7/+9S8AsBA3APDee+9h/fr16NixI4YPH44WLVogKysLe/bsQUpKitkt+M9//hPff/89nn/+eaxfvx5du3ZFcXEx0tPT8f3335vrG3maqKgoTJgwAVOmTMFDDz2Efv36ma95+/btzUGK1atXx9SpUzFy5Eg8+OCDGDRoEE6ePIlFixZZxYPcdddd6NSpEyZMmICsrCzUrFkTS5cuNVs0JH5+fpg7dy769u2LNm3a4Nlnn0VMTAzS09Nx8OBBrF27FoD9e6hl6tSp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\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "movie_budget.corr()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 355
        },
        "id": "CzjUka5nyP1_",
        "outputId": "939e449f-9e8f-4c2c-efef-d2b2054b0f1f"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "<ipython-input-55-d9e7636924a1>:1: FutureWarning: The default value of numeric_only in DataFrame.corr is deprecated. In a future version, it will default to False. Select only valid columns or specify the value of numeric_only to silence this warning.\n",
            "  movie_budget.corr()\n"
          ]
        },
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                   production_budget  domestic_gross  worldwide_gross  \\\n",
              "production_budget           1.000000        0.685682         0.748306   \n",
              "domestic_gross              0.685682        1.000000         0.938853   \n",
              "worldwide_gross             0.748306        0.938853         1.000000   \n",
              "month                       0.022575        0.028034         0.030288   \n",
              "year                        0.176091        0.036690         0.100588   \n",
              "day                        -0.019217       -0.041380        -0.029274   \n",
              "total_gross                 0.739912        0.968058         0.995194   \n",
              "net_gross                   0.643580        0.965476         0.983933   \n",
              "\n",
              "                      month      year       day  total_gross  net_gross  \n",
              "production_budget  0.022575  0.176091 -0.019217     0.739912   0.643580  \n",
              "domestic_gross     0.028034  0.036690 -0.041380     0.968058   0.965476  \n",
              "worldwide_gross    0.030288  0.100588 -0.029274     0.995194   0.983933  \n",
              "month              1.000000 -0.020533  0.100438     0.030028   0.029689  \n",
              "year              -0.020533  1.000000  0.034229     0.083681   0.060296  \n",
              "day                0.100438  0.034229  1.000000    -0.033085  -0.033833  \n",
              "total_gross        0.030028  0.083681 -0.033085     1.000000   0.991066  \n",
              "net_gross          0.029689  0.060296 -0.033833     0.991066   1.000000  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-bbd7763a-1b9f-4ba0-bf6c-4f1454ce4b87\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>production_budget</th>\n",
              "      <th>domestic_gross</th>\n",
              "      <th>worldwide_gross</th>\n",
              "      <th>month</th>\n",
              "      <th>year</th>\n",
              "      <th>day</th>\n",
              "      <th>total_gross</th>\n",
              "      <th>net_gross</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>production_budget</th>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.685682</td>\n",
              "      <td>0.748306</td>\n",
              "      <td>0.022575</td>\n",
              "      <td>0.176091</td>\n",
              "      <td>-0.019217</td>\n",
              "      <td>0.739912</td>\n",
              "      <td>0.643580</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>domestic_gross</th>\n",
              "      <td>0.685682</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.938853</td>\n",
              "      <td>0.028034</td>\n",
              "      <td>0.036690</td>\n",
              "      <td>-0.041380</td>\n",
              "      <td>0.968058</td>\n",
              "      <td>0.965476</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>worldwide_gross</th>\n",
              "      <td>0.748306</td>\n",
              "      <td>0.938853</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.030288</td>\n",
              "      <td>0.100588</td>\n",
              "      <td>-0.029274</td>\n",
              "      <td>0.995194</td>\n",
              "      <td>0.983933</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>month</th>\n",
              "      <td>0.022575</td>\n",
              "      <td>0.028034</td>\n",
              "      <td>0.030288</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>-0.020533</td>\n",
              "      <td>0.100438</td>\n",
              "      <td>0.030028</td>\n",
              "      <td>0.029689</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>year</th>\n",
              "      <td>0.176091</td>\n",
              "      <td>0.036690</td>\n",
              "      <td>0.100588</td>\n",
              "      <td>-0.020533</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.034229</td>\n",
              "      <td>0.083681</td>\n",
              "      <td>0.060296</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>day</th>\n",
              "      <td>-0.019217</td>\n",
              "      <td>-0.041380</td>\n",
              "      <td>-0.029274</td>\n",
              "      <td>0.100438</td>\n",
              "      <td>0.034229</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>-0.033085</td>\n",
              "      <td>-0.033833</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>total_gross</th>\n",
              "      <td>0.739912</td>\n",
              "      <td>0.968058</td>\n",
              "      <td>0.995194</td>\n",
              "      <td>0.030028</td>\n",
              "      <td>0.083681</td>\n",
              "      <td>-0.033085</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.991066</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>net_gross</th>\n",
              "      <td>0.643580</td>\n",
              "      <td>0.965476</td>\n",
              "      <td>0.983933</td>\n",
              "      <td>0.029689</td>\n",
              "      <td>0.060296</td>\n",
              "      <td>-0.033833</td>\n",
              "      <td>0.991066</td>\n",
              "      <td>1.000000</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-bbd7763a-1b9f-4ba0-bf6c-4f1454ce4b87')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-bbd7763a-1b9f-4ba0-bf6c-4f1454ce4b87 button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-bbd7763a-1b9f-4ba0-bf6c-4f1454ce4b87');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 55
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "movie_budget.isna().sum()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "KkFYqIFnwj0S",
        "outputId": "b0e54e22-d5c1-44ba-835c-d43cf8a46cd2"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "release_date         0\n",
              "movie                0\n",
              "production_budget    0\n",
              "domestic_gross       0\n",
              "worldwide_gross      0\n",
              "month                0\n",
              "year                 0\n",
              "day                  0\n",
              "total_gross          0\n",
              "net_gross            0\n",
              "dtype: int64"
            ]
          },
          "metadata": {},
          "execution_count": 56
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "movie_budget.shape"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "ZjtIeQWh8d_A",
        "outputId": "bbc50dda-bbae-4d53-f6ce-e0bb9ef921b4"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "(5782, 10)"
            ]
          },
          "metadata": {},
          "execution_count": 57
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Load the bom_movie data."
      ],
      "metadata": {
        "id": "FmlG0CDIR8_f"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "bom_movie = pd.read_csv('/content/bom.movie_gross.csv')\n",
        "bom_movie.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 206
        },
        "id": "4Su7yLNov-Kq",
        "outputId": "2ad3e0b9-841f-4c18-a029-3997b75c2afb"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                                         title studio  domestic_gross  \\\n",
              "0                                  Toy Story 3     BV     415000000.0   \n",
              "1                   Alice in Wonderland (2010)     BV     334200000.0   \n",
              "2  Harry Potter and the Deathly Hallows Part 1     WB     296000000.0   \n",
              "3                                    Inception     WB     292600000.0   \n",
              "4                          Shrek Forever After   P/DW     238700000.0   \n",
              "\n",
              "  foreign_gross  year  \n",
              "0     652000000  2010  \n",
              "1     691300000  2010  \n",
              "2     664300000  2010  \n",
              "3     535700000  2010  \n",
              "4     513900000  2010  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-594b2481-409c-4790-8cea-b7746deebfab\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>title</th>\n",
              "      <th>studio</th>\n",
              "      <th>domestic_gross</th>\n",
              "      <th>foreign_gross</th>\n",
              "      <th>year</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>Toy Story 3</td>\n",
              "      <td>BV</td>\n",
              "      <td>415000000.0</td>\n",
              "      <td>652000000</td>\n",
              "      <td>2010</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>Alice in Wonderland (2010)</td>\n",
              "      <td>BV</td>\n",
              "      <td>334200000.0</td>\n",
              "      <td>691300000</td>\n",
              "      <td>2010</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>Harry Potter and the Deathly Hallows Part 1</td>\n",
              "      <td>WB</td>\n",
              "      <td>296000000.0</td>\n",
              "      <td>664300000</td>\n",
              "      <td>2010</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>Inception</td>\n",
              "      <td>WB</td>\n",
              "      <td>292600000.0</td>\n",
              "      <td>535700000</td>\n",
              "      <td>2010</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>Shrek Forever After</td>\n",
              "      <td>P/DW</td>\n",
              "      <td>238700000.0</td>\n",
              "      <td>513900000</td>\n",
              "      <td>2010</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-594b2481-409c-4790-8cea-b7746deebfab')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-594b2481-409c-4790-8cea-b7746deebfab button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-594b2481-409c-4790-8cea-b7746deebfab');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 58
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Add a New columns showing the total gross earning per movie"
      ],
      "metadata": {
        "id": "udVMJgk2SHDi"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "bom_movie['foreign_gross'] = bom_movie['foreign_gross'].str.replace(',','')\n",
        "bom_movie['foreign_gross'] = pd.to_numeric(bom_movie['foreign_gross'])"
      ],
      "metadata": {
        "id": "bYL4QOHD-Rgd"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "bom_movie['total_gross'] = bom_movie['domestic_gross'] + bom_movie['foreign_gross']\n",
        "bom_movie.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 206
        },
        "id": "xG7HFdWc-qQa",
        "outputId": "6e013621-5deb-40a5-a175-628d5c795b05"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                                         title studio  domestic_gross  \\\n",
              "0                                  Toy Story 3     BV     415000000.0   \n",
              "1                   Alice in Wonderland (2010)     BV     334200000.0   \n",
              "2  Harry Potter and the Deathly Hallows Part 1     WB     296000000.0   \n",
              "3                                    Inception     WB     292600000.0   \n",
              "4                          Shrek Forever After   P/DW     238700000.0   \n",
              "\n",
              "   foreign_gross  year   total_gross  \n",
              "0    652000000.0  2010  1.067000e+09  \n",
              "1    691300000.0  2010  1.025500e+09  \n",
              "2    664300000.0  2010  9.603000e+08  \n",
              "3    535700000.0  2010  8.283000e+08  \n",
              "4    513900000.0  2010  7.526000e+08  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-7e14753f-5886-4585-a0ab-6ec8d4873787\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>title</th>\n",
              "      <th>studio</th>\n",
              "      <th>domestic_gross</th>\n",
              "      <th>foreign_gross</th>\n",
              "      <th>year</th>\n",
              "      <th>total_gross</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>Toy Story 3</td>\n",
              "      <td>BV</td>\n",
              "      <td>415000000.0</td>\n",
              "      <td>652000000.0</td>\n",
              "      <td>2010</td>\n",
              "      <td>1.067000e+09</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>Alice in Wonderland (2010)</td>\n",
              "      <td>BV</td>\n",
              "      <td>334200000.0</td>\n",
              "      <td>691300000.0</td>\n",
              "      <td>2010</td>\n",
              "      <td>1.025500e+09</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>Harry Potter and the Deathly Hallows Part 1</td>\n",
              "      <td>WB</td>\n",
              "      <td>296000000.0</td>\n",
              "      <td>664300000.0</td>\n",
              "      <td>2010</td>\n",
              "      <td>9.603000e+08</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>Inception</td>\n",
              "      <td>WB</td>\n",
              "      <td>292600000.0</td>\n",
              "      <td>535700000.0</td>\n",
              "      <td>2010</td>\n",
              "      <td>8.283000e+08</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>Shrek Forever After</td>\n",
              "      <td>P/DW</td>\n",
              "      <td>238700000.0</td>\n",
              "      <td>513900000.0</td>\n",
              "      <td>2010</td>\n",
              "      <td>7.526000e+08</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-7e14753f-5886-4585-a0ab-6ec8d4873787')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-7e14753f-5886-4585-a0ab-6ec8d4873787 button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-7e14753f-5886-4585-a0ab-6ec8d4873787');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 60
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "bom_movie.corr()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 229
        },
        "id": "3ZHSpLCJWlGP",
        "outputId": "500a567c-410f-4237-bd14-755824ff8886"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "<ipython-input-61-a66b3eb6edc1>:1: FutureWarning: The default value of numeric_only in DataFrame.corr is deprecated. In a future version, it will default to False. Select only valid columns or specify the value of numeric_only to silence this warning.\n",
            "  bom_movie.corr()\n"
          ]
        },
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                domestic_gross  foreign_gross      year  total_gross\n",
              "domestic_gross        1.000000       0.767991  0.018708     0.904548\n",
              "foreign_gross         0.767991       1.000000  0.145653     0.967759\n",
              "year                  0.018708       0.145653  1.000000     0.143127\n",
              "total_gross           0.904548       0.967759  0.143127     1.000000"
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-d77ad1bc-841e-4344-9ed0-cae077931b6d\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>domestic_gross</th>\n",
              "      <th>foreign_gross</th>\n",
              "      <th>year</th>\n",
              "      <th>total_gross</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>domestic_gross</th>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.767991</td>\n",
              "      <td>0.018708</td>\n",
              "      <td>0.904548</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>foreign_gross</th>\n",
              "      <td>0.767991</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.145653</td>\n",
              "      <td>0.967759</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>year</th>\n",
              "      <td>0.018708</td>\n",
              "      <td>0.145653</td>\n",
              "      <td>1.000000</td>\n",
              "      <td>0.143127</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>total_gross</th>\n",
              "      <td>0.904548</td>\n",
              "      <td>0.967759</td>\n",
              "      <td>0.143127</td>\n",
              "      <td>1.000000</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-d77ad1bc-841e-4344-9ed0-cae077931b6d')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-d77ad1bc-841e-4344-9ed0-cae077931b6d button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-d77ad1bc-841e-4344-9ed0-cae077931b6d');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 61
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "A better understanding of your competitor(s) will position Microsoft at a better place through improving their current models.More analysis is required to better understand the business strategies, business models and their go to market channels(Distribution chain)"
      ],
      "metadata": {
        "id": "5JVEF2-HQh0G"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "top_studio = bom_movie[\"studio\"].unique()[:10]\n",
        "top_studio_counts = bom_movie[\"studio\"].value_counts().nlargest(10).tolist()\n",
        "movie_rel_year = bom_movie['year'].unique()\n",
        "top_studio_gross = bom_movie['total_gross'].sum()\n",
        "\n",
        "print(\"Studio:\", top_studio)\n",
        "print(\"Counts:\", top_studio_counts)\n",
        "print(\"Years:\", movie_rel_year)\n",
        "print(\"gross:\", top_studio_gross)"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "UmeI1tHxi9XV",
        "outputId": "d7f81368-3c34-4ca9-aa53-4214b46af0fa"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Studio: ['BV' 'WB' 'P/DW' 'Sum.' 'Par.' 'Uni.' 'Fox' 'Wein.' 'Sony' 'FoxS']\n",
            "Counts: [166, 147, 140, 136, 136, 123, 110, 106, 103, 101]\n",
            "Years: [2010 2011 2012 2013 2014 2015 2016 2017 2018]\n",
            "gross: 246486889161.5\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#Based on correlation alone, domestic gross earnings and foreign gross earnings have a relatively strong positive relationship.\n",
        "sns.scatterplot(x='domestic_gross',y='foreign_gross',data = bom_movie,color='blue').set_title('Correlation between Domestic gross and Foreign gross')"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 504
        },
        "id": "wGC8ksRtSfPV",
        "outputId": "b4079cff-de10-470e-cd36-b4a27e467411"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "Text(0.5, 1.0, 'Correlation between Domestic gross and Foreign gross')"
            ]
          },
          "metadata": {},
          "execution_count": 63
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "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\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "# A glance of the Top 10 Movie Studios\n",
        "bar_chart_title = \"Top 10 Most Common Movie Studio\"\n",
        "\n",
        "fig, ax = plt.subplots()\n",
        "\n",
        "\n",
        "ax.bar(top_studio,top_studio_counts)\n",
        "ax.set_xlabel('Studio')\n",
        "ax.set_ylabel('Movies released')\n",
        "ax.set_title(bar_chart_title)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 489
        },
        "id": "Z6XPGd95wLUY",
        "outputId": "2cbf8ee7-fdf8-4a3f-8ea9-109aa49aecdc"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "Text(0.5, 1.0, 'Top 10 Most Common Movie Studio')"
            ]
          },
          "metadata": {},
          "execution_count": 64
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 640x480 with 1 Axes>"
            ],
            "image/png": "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ww4RERHJGsMOERERyRrDDhEREckaww4RERHJGsMOERERyRrDDhEREckaww4RERHJGsMOERERyRrDDhEREckaww4RERHJGsMOERERyRrDDhEREckaww4RERHJGsMOERERyRrDDhEREckaww4RERHJGsMOERERyRrDDhEREckaww4RERHJGsMOERERyZpsws6aNWvg7OwMAwMDuLu7IyEhoa5LIiIiIg0gi7CzdetWzJ49GwsXLkRSUhLat28PX19fZGVl1XVpREREVMdkEXY+//xzTJ48GRMnToSbmxsiIiJgZGSEb7/9tq5LIyIiojpW78POo0ePkJiYCB8fH6lNS0sLPj4+iI+Pr8PKiIiISBPo1HUB1fXvv/+iuLgYNjY2Su02Njb466+/yl2msLAQhYWF0uPc3FwAQF5entrrKym8r/Z1VldltpN1qw/rrl2su3ax7tol57qrs14hxPM7inru5s2bAoA4ceKEUvucOXNEt27dyl1m4cKFAgAnTpw4ceLESQZTWlrac7NCvT+y07BhQ2hrayMzM1OpPTMzE7a2tuUuM3/+fMyePVt6XFJSguzsbFhZWUGhUNRovVWVl5cHBwcHpKWlwczMrK7LqTTWXbtYd+1i3bWLddeu+lC3EAL37t2Dvb39c/vV+7Cjp6eHzp074/Dhwxg8eDCAJ+Hl8OHDmDFjRrnL6OvrQ19fX6nNwsKihitVDzMzM4190z0P665drLt2se7axbprl6bXbW5u/sI+9T7sAMDs2bMxfvx4dOnSBd26dUN4eDgKCgowceLEui6NiIiI6pgsws6IESNw+/ZtLFiwABkZGejQoQMOHjxYZtAyERER/e+RRdgBgBkzZlR42koO9PX1sXDhwjKn3zQd665drLt2se7axbprV32tuzwKIV50vRYRERFR/VXvbypIRERE9DwMO0RERCRrDDtEREQkaww7RERq5uzsjPDw8LouQ9ZiY2OhUCiQk5NT16VQPcCwo0EmTJgAhUIhTVZWVujbty/Onz+P5cuXo0GDBnj48GGZ5e7fvw8zMzOsXLmy1mqNiIiAqakpHj9+LLXl5+dDV1cXXl5eSn1LP5SuXbsGZ2dnafu0tbVhb2+PwMBA3L17V221Pf066unpoXnz5ggJCVGqNS4uDg4ODmX66+rqwsbGBr1798a3336LkpISaZmRI0eib9++Ss918OBBKBQKLFq0SKl90aJFcHR0rFL9t2/fxtSpU+Ho6Ah9fX3Y2trC19cXx48fr9L66lJl9oUm8fLyQlBQUJn2yMhIlW48eurUKUyZMkV9hVXSs58hpdPVq1drvZanVfXz4nleeeUVpKenV+qGcupSX383a/J9kZKSgtGjR8Pe3h4GBgZo3Lgx/P39K/xuyrrCsKNh+vbti/T0dKSnp+Pw4cPQ0dHBgAEDMHbsWBQUFGDHjh1lltm+fTsePXqEMWPG1Fqd3t7eyM/Px+nTp6W2Y8eOwdbWFidPnlQKZTExMXB0dESzZs0AACEhIUhPT0dqaio2bdqEo0ePYubMmWqtr/R1vHLlCt577z0sWrQIn332mTR/9+7dGDhwYJn+169fx4EDB+Dt7Y13330XAwYMkD6gvb29cfz4caUP7JiYGDg4OCA2Nlbp+WNiYuDt7V2l2ocOHYozZ84gKioKly9fxp49e+Dl5YU7d+5UaX117UX7orKKi4uVwqcms7a2hpGRUZ0899OfIaVTkyZN6qSWUtX5vKiInp4ebG1ta/Urfurz72ZNvC+KiorQu3dv5ObmYseOHbh06RK2bt2Ktm3bat4RN/V8HSepw/jx44W/v79S27FjxwQAkZWVJYYMGSJ69epVZjlPT08xYsSIWqry/9nZ2YnQ0FDp8dy5c8X06dOFq6uriImJkdp79Oghxo8fL4QQwsnJSaxYsUJpPf/973+Fm5ub2uoq73Xs3bu3ePnll6XHzZo1EwcOHKiwvxBCHD58WAAQ69evF0IIcenSJQFAxMfHS326desm1qxZIwwMDMSDBw+EEEI8ePBA6Ovriw0bNqhc+927dwUAERsbW+78lJQUAUCcOXOmzDKlr3lMTIwAIA4ePCg6dOggDAwMhLe3t8jMzBQ///yzcHFxEaampmLUqFGioKBA5RpV8bx9sXz5ctGmTRthZGQkGjduLKZOnSru3bsn9duwYYMwNzcXu3fvFq6urkJbW1ukpKTUaL2enp7i3XffLdNeWosQ/79Nn332mbC1tRWWlpZi2rRp4tGjR1L/8t7ntaGi97IQQsTGxoquXbsKPT09YWtrKz744ANRVFQkhBAiKipKGBsbi8uXL0v9p06dKlq1aqW294iqnxfFxcXik08+Ec7OzsLAwEC0a9dObNu2TepX+j6/e/euEOL/99HBgweFi4uLMDY2Fr6+vuLWrVtqqf9Fv5tCCHHjxg0xaNAgYWxsLExNTcUbb7whMjIypPkLFy4U7du3Fxs3bhROTk7CzMxMjBgxQuTl5QkhnuwHS0tL8fDhQ6X1+vv7izFjxlS59pp6X5w5c0YAENevX69ybbWFR3Y0WH5+Pr7//ns0b94cVlZWCAwMxJEjR3Djxg2pz99//42jR48iMDCw1uvz9vZGTEyM9DgmJgZeXl7w9PSU2h88eICTJ09WeJTj5s2b2Lt3L9zd3Wu0VkNDQzx69AgAcOHCBWRlZaFnz57PXaZnz55o3769dDStZcuWsLe3l7bt3r17SEpKwhtvvAFnZ2fEx8cDAE6cOIHCwsIqHdkxMTGBiYkJdu3ahcLCQpWXf9qiRYuwevVqnDhxAmlpaRg+fDjCw8OxefNm7N+/H4cOHcKqVauq9RxVUbovtLS0sHLlSly4cAFRUVE4cuQI5s6dq9T3/v37CAsLw9dff40LFy6gUaNGtV5veWJiYnDt2jXExMQgKioKkZGRiIyMrOuyKnTz5k3069cPXbt2xblz57Bu3Tp88803WLx4MQBg3Lhx6NevHwICAvD48WPs378fX3/9NTZt2qS2I1Sqfl6EhoZi48aNiIiIwIULFzBr1iyMGTMGcXFxFT7H/fv3sWzZMnz33Xc4evQoUlNT8f7776ul/hf9bpaUlMDf3x/Z2dmIi4tDdHQ0/v77b4wYMUKp37Vr17Br1y7s27cP+/btQ1xcHD799FMAwBtvvIHi4mLs2bNH6p+VlYX9+/dj0qRJatmOp1X3fWFtbQ0tLS1s374dxcXFaq9Preo6bdH/Gz9+vNDW1hbGxsbC2NhYABB2dnYiMTFRCCHE48ePxUsvvSQWLlwoLRMcHCwcHR1FcXFxrde7fv16YWxsLIqKikReXp7Q0dERWVlZYvPmzaJHjx5CiP8/OnLjxg0hxJP/ePX09ISxsbEwMDAQAIS7u7v035k6PP1fTElJiYiOjhb6+vri/fffF0IIsWTJEjFs2LBy+z9rxIgRwtXVVXocEBAg+vTpI4QQYv/+/dIRqSlTpogFCxYIIZ7skyZNmlS5/u3bt4sGDRoIAwMD8corr4j58+eLc+fOCSFUO7Lz66+/Sn1CQ0MFAHHt2jWp7a233hK+vr5VrrMyXrQvnrZt2zZhZWUlPd6wYYMAIM6ePVujNT6tskd2nJycxOPHj6X5b7zxhtLR1bo8svP0Z4ixsbEYNmyY+M9//iNatWolSkpKpL5r1qwRJiYm0mdHdna2dITNxsZGLFmyRK21qfJ5cf36dWFkZCROnDihtI7AwEAxatQoIUT5R3YAiKtXrypto42Njdq24Xm/m4cOHRLa2toiNTVV6n/hwgUBQCQkJAghnhzZMTIyko7kCCHEnDlzhLu7u/R46tSpws/PT3q8fPly0bRpU6V9p6qafF+sXr1aGBkZCVNTU+Ht7S1CQkKUPmc0BY/saBhvb2+cPXsWZ8+eRUJCAnx9feHn54cbN25AW1sb48ePR2RkJIQQKCkpQVRUFCZOnAgtrdrflV5eXigoKMCpU6dw7NgxtGzZEtbW1vD09JTOw8fGxqJp06ZKg3XnzJmDs2fP4vz58zh8+DAAoH///mr9z2Dfvn0wMTGBgYEB/Pz8MGLECGkQ8e7duzFo0KBKrUcIoTQmwMvLC8ePH0dRURFiY2OlwZWenp7SuJ3Y2Ngqj9cBnowLuHXrFvbs2YO+ffsiNjYWnTp1UvnIQbt27aSfbWxsYGRkhKZNmyq1ZWVlVbnOyqpoX/z666/o1asXXnrpJZiammLs2LG4c+cO7t+/Ly2rp6entB2aonXr1tDW1pYe29nZ1cprWRlPf4acPXsWK1euRHJyMjw8PJTey6+++iry8/Pxzz//AAAaNGiAb775BuvWrUOzZs0wb948tdalyudFfn4+7t+/j969e0tHVExMTLBx48bnDlw2MjJSGuuj7v3yvN/N5ORkODg4SBc+AICbmxssLCyQnJwstTk7O8PU1LTCGidPnoxDhw7h5s2bAJ4Mji8dYFwdNfW+mD59OjIyMrBp0yZ4eHhg27ZtaN26NaKjo6tVr7ox7GgYY2NjNG/eHM2bN0fXrl3x9ddfo6CgAOvXrwcATJo0CampqThy5AgOHz6MtLS0Ovt29+bNm6Nx48aIiYlBTEwMPD09AQD29vZwcHDAiRMnEBMTU+Z0UcOGDdG8eXO0aNECPXv2RHh4uNRXXUp/sa9cuYIHDx4gKioKxsbGSE9Px5kzZ9C/f/9KrSc5OVlpEJ+3t7f0gf30Npd+YGdnZ+PkyZMvPEX2IgYGBujduzeCg4Nx4sQJTJgwAQsXLpRCrXjqW16KiorKXYeurq70c+mVZk9TKBS1MuC3vH1x+/ZtDBgwAO3atcNPP/2ExMRErFmzBgCk043Ak1NetTkA1czMDLm5uWXac3JylK76qavXsjKe/gxp3rw57OzsKr3s0aNHoa2tjfT0dBQUFKi1LlU+L/Lz8wEA+/fvV/oDffHiRWzfvr3C5yhvvwg1fyNSRb+blfWi907Hjh3Rvn17bNy4EYmJibhw4QImTJhQ7bpr8n1hamqKgQMHYsmSJTh37hxee+016VSYpmDY0XAKhQJaWlp48OABAKBZs2bw9PTEt99+iw0bNsDHxwdOTk51Vp+3tzdiY2OVjnIAQI8ePXDgwAEkJCS88ChH6X/IpduoDqW/2I6OjtDR+f/vu927dy9eeeUVWFpavnAdR44cwR9//IGhQ4dKbc2aNYODgwP27NmDs2fPSh/YL730El566SUsX74cjx49qtaRnfK4ubmhoKAA1tbWAID09HRp3tmzZ9X6XOpW3r5ITExESUkJli9fjpdffhktW7bErVu36rhSoFWrVkhKSirTnpSUhJYtW9ZBRerh6uqK+Ph4pT/8x48fh6mpKRo3bgzgyVizsLAw7N27FyYmJjXyxcqV/bxwc3ODvr4+UlNTlf5AN2/eXOnIiSYo/d10dXVFWloa0tLSpHkXL15ETk4O3NzcVFrnm2++icjISOkzvqa2uSbeFwqFAi4uLmoPy9XFsKNhCgsLkZGRgYyMDCQnJ+Odd95Bfn6+0mXSgYGB2LFjB3bu3FknA5Of5u3tjd9++03pDz/w5EjHl19+We4f/nv37iEjIwPp6elISEjAnDlzYG1tjVdeeaXG692zZ0+5p7BKX/ebN28iKSkJn3zyCfz9/TFgwACMGzdOqa+3tzfWrl2L5s2bw8bGRmr39PTEqlWrpIHMVXHnzh307NkT33//Pc6fP4+UlBRs27YNS5cuhb+/PwwNDfHyyy/j008/RXJyMuLi4vDRRx9V6bmetXr1avTq1Ust63qR5s2bo6ioCKtWrcLff/+N7777DhERES9cbv78+WX2hzpNnToVly9fxsyZM3H+/HlcunQJn3/+ObZs2YL33nuvyusdN24c5s+fr8ZKVTNt2jSkpaXhnXfewV9//YXdu3dj4cKFmD17NrS0tHDv3j2MHTsWM2fOhJ+fHzZt2oStW7c+9yhKVVT288LU1BTvv/8+Zs2ahaioKFy7dg1JSUlYtWoVoqKiqvz8O3fuhIuLS5WWfdHvpo+PD9q2bYuAgAAkJSUhISEB48aNg6enJ7p06aLSc40ePRr//PMP1q9fXyMDk0tV931x9uxZ+Pv7Y/v27bh48SKuXr2Kb775Bt9++y38/f1rrO4qqcsBQ6Rs/PjxAoA0mZqaiq5du4rt27cr9bt//74wNzcv9xLF2lY6YNbFxUWp/fr16wKAaNWqlVK7k5OT0jZaW1uLfv36KQ24ra6KBhzn5+cLAwMDceXKlTL9S+vR0dER1tbWwsfHR3z77bflDvwuHQj59ttvK7VHRkYKAOKtt96qcu0PHz4U8+bNE506dRLm5ubCyMhItGrVSnz00Ufi/v37QgghLl68KDw8PIShoaHo0KGDOHToULkDlJ8e9P30ANtSpZfBPv3YycmpyrWX53mDvz///HNhZ2cnDA0Nha+vr9i4cWO5lxI/uz5PT0+11vishIQE0bt3b2FtbS3Mzc2Fu7u72Llzp1INz27Tu+++q1TXswOUPT09pdsv1KSqXmI8ceJE0bZtW6XPk+XLlwtLS0vxzz//qK0+VT4vSkpKRHh4uGjVqpXQ1dUV1tbWwtfXV8TFxQkhKr70/Gk7d+4UT/+ZK/3drYrK/G5W9tLzp61YsaLc37uxY8eq7TO+pt4Xt2/fFjNnzhRt2rQRJiYmwtTUVLRt21YsW7asTi6aeR6FEGo+oUmkoXbs2IGPPvoIFy9erOtSiIieq1evXmjdunWt3hlfznRe3IVIHkxMTBAWFlbXZRARVeju3bvSuKa1a9fWdTmywSM7REREGsLZ2Rl3795FcHCw2m6ISAw7REREJHO8GouIiIhkjWGHiIiIZI1hh4iIiGSNYYeIiIhkjWGHiP6neXl5ISgoSHrs7OyM8PDwOquHiNSPYYeINM7t27cxdepUODo6Ql9fH7a2tvD19cXx48cBPPn+nV27dtXIc586dQpTpkypkXUTUd3gTQWJSOMMHToUjx49QlRUFJo2bYrMzEwcPnwYd+7cqfHnLv2yVSKSDx7ZISKNkpOTg2PHjiEsLAze3t5wcnJCt27dMH/+fAwaNAjOzs4AgNdffx0KhUJ6PGHCBAwePFhpXUFBQUrfrl1QUIBx48bBxMQEdnZ2WL58eZnnf/Y0VmpqKvz9/WFiYgIzMzMMHz4cmZmZat5qIqpJDDtEpFFMTExgYmKCXbt2obCwsMz8U6dOAQA2bNiA9PR06XFlzJkzB3Fxcdi9ezcOHTqE2NhYJCUlVdi/pKQE/v7+yM7ORlxcHKKjo/H3339jxIgRqm8YEdUZnsYiIo2io6ODyMhITJ48GREREejUqRM8PT0xcuRItGvXTjrNZGFhAVtb20qvNz8/H9988w2+//579OrVCwAQFRWFxo0bV7jM4cOH8ccffyAlJQUODg4AgI0bN6J169Y4deoUunbtWo0tJaLawiM7RKRxhg4dilu3bmHPnj3o27cvYmNj0alTJ0RGRlZ5ndeuXcOjR4/g7u4utVlaWqJVq1YVLpOcnAwHBwcp6ACAm5sbLCwskJycXOVaiKh2MewQkUYyMDBA7969ERwcjBMnTmDChAlYuHBhhf21tLTw7Ff9FRUV1XSZRFQPMOwQUb3g5uaGgoICAICuri6Ki4uV5ltbWyM9PV2p7ezZs9LPzZo1g66uLk6ePCm13b17F5cvX67wOV1dXZGWloa0tDSp7eLFi8jJyYGbm1t1NoeIahHDDhFplDt37qBnz574/vvvcf78eaSkpGDbtm1YunQp/P39ATy5Yurw4cPIyMjA3bt3AQA9e/bE6dOnsXHjRly5cgULFy7En3/+Ka3XxMQEgYGBmDNnDo4cOYI///wTEyZMgJZWxR+DPj4+aNu2LQICApCUlISEhASMGzcOnp6e6NKlS82+EESkNgw7RKRRTExM4O7ujhUrVqBHjx5o06YNgoODMXnyZKxevRoAsHz5ckRHR8PBwQEdO3YEAPj6+iI4OBhz585F165dce/ePYwbN05p3Z999hlee+01DBw4ED4+PujevTs6d+5cYS0KhQK7d+9GgwYN0KNHD/j4+KBp06bYunVrzb0ARKR2CvHsSW4iIiIiGeGRHSIiIpI1hh0iIiKSNYYdIiIikjWGHSIiIpI1hh0iIiKSNYYdIiIikjWGHSIiIpI1hh0iIiKSNYYdIiIikjWGHSIiIpI1hh0iIiKSNYYdIiIikrX/A3wNiEc0Su5xAAAAAElFTkSuQmCC\n"
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "#bar_chart_title = \"Top 10 Most Common Movie Studio\"\n",
        "\n",
        "#fig, ax = plt.subplots()\n",
        "\n",
        "\n",
        "#ax.bar(movie_rel_year , top_studio)\n",
        "##ax.set_xlabel('Release_Year')\n",
        "#ax.set_ylabel('Studio')\n",
        "#ax.set_title(bar_chart_title)"
      ],
      "metadata": {
        "id": "EP-rEXCPnt1q"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "movie_rel_year = bom_movie['year'].unique()\n",
        "movie_rel_year"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "t5NeCNL9x4Xy",
        "outputId": "d2b3f23b-a093-4f2a-c607-23115f822cd7"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "array([2010, 2011, 2012, 2013, 2014, 2015, 2016, 2017, 2018])"
            ]
          },
          "metadata": {},
          "execution_count": 66
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Recommendations\n",
        "\n",
        "Pursue and R rated Movie category"
      ],
      "metadata": {
        "id": "2v1MYayawGzi"
      }
    }
  ],
  "metadata": {
    "kernelspec": {
      "display_name": "Python 3",
      "language": "python",
      "name": "python3"
    },
    "language_info": {
      "codemirror_mode": {
        "name": "ipython",
        "version": 3
      },
      "file_extension": ".py",
      "mimetype": "text/x-python",
      "name": "python",
      "nbconvert_exporter": "python",
      "pygments_lexer": "ipython3",
      "version": "3.6.4"
    },
    "colab": {
      "provenance": [],
      "include_colab_link": true
    }
  },
  "nbformat": 4,
  "nbformat_minor": 0
}