## Determining-ICO-Success-Parameters-

<head>

</head>
<body>
	<div class="banner">
		<img src="https://opengeekslab.com/wp-content/uploads/2021/10/Definition-of-an-ICO-and-Its-Types.png" alt="ICO Types Banner">
	</div>
</body>



This repository contains code and data for determining the parameters of success on Initial Coin Offerings (ICOs) through descriptive and predictive analysis. The project is divided into four parts as described below:

Part I
In this part, we analyze the data on ICOs and visualize the connections between different variables to determine their effect on the success and performance of the ICOs. We observe that the success of an ICO largely depends on the amount raised during the offering and the soft cap of the ICO. We also find that the amount raised increases with ratings provided by experts and the number of team members, but decreases with an increase in the number of experts providing the ratings.

We treat the missing values in the data set by putting in the average values from the data set for numeric missing values including duration, number of team members, number of experts, etc. We replace the missing values in softcap and hardcap with zeros assuming that the ICO is not launched if the minimum amount is not met. We create a new country category as "None" to treat the missing values in restricted countries, and drop the rows with missing values in the token field.

We split the data into a 70:30 train/test ratio for regression purposes with the independent variables as those factors which visually appear to have a substantial effect on the amount raised, namely 'Token', 'Softcap', 'Hardcap', 'Start', 'End', 'Quarterstart', 'Duration', 'Country', 'ERC20', 'Rating', and '#Experts. The dependent variable is the amount raised. Dummy variables are created for categorical variables.

Part II
In this part, we create a new variable called "Success" that gives a binary value of 1 if the ICO ascends to the soft cap or if it fails to do so but the amount raised is greater than 0.5 million dollars. Otherwise, the ICO is deemed unsuccessful. We use the IF function to test the values and generate a new column of success for each ICO.

We conduct a graphical analysis of the variables to determine which variables are the most important in deciding the success of the ICO. We find that amount raised and softcap are the most important ones because the success criterion is derived from the two variables. Other variables that appear to increase the success of the ICO are accepted fiat, presales, number of experts, number of team members, ratings, number of bonuses, and the existence of US restrictions.

We generate a heatmap to visualize the correlation among all the variables. Except for the correlation between softcap and hardcap, there is a negligible correlation between any pair of variables.

Using the significant variables of softcap, rating, #experts, bonus, #teammembers, US_Restriction, accepted_fiat, presale, and amount_raised, we conduct K-Means clustering to determine the success of the ICOs. Using the Elbow Method, the optimal number of clusters is shown to be 2. Indeed, as seen in the table below, the mean values vary the most significantly when it comes to the aforementioned variables.

<table>
  <tr>
    <th>Variable</th>
    <th>Cluster 0</th>
    <th>Cluster 1</th>
  </tr>
  <tr>
    <td>SoftCap</td>
    <td>19695759.93</td>
    <td>15571701.31</td>
  </tr>
  <tr>
    <td>HardCap</td>
    <td>92190969.77</td>
    <td>93671788.03</td>
  </tr>
  <tr>
    <td>Duration</td>
    <td>62.28</td>
    <td>44.86</td>
  </tr>
  <tr>
    <td>ERC20</td>
    <td>0.81</td>
    <td>0.71</td>
  </tr>
  <tr>
    <td>Rating</td>
    <td>3.68</td>
    <td>2.73</td>
  </tr>
  <tr>
    <td>Experts</td>
    <td>8.84</td>
    <td>1.51</td>
  </tr>
  <tr>
    <td>Bonus</td>
    <td>0.74</td>
    <td>0.21</td>
  </tr>
  <tr>
    <td>#Team Members</td>
    <td>12.</td>
    <td></td>
  </tr>
</table>
