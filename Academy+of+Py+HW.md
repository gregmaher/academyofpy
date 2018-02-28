

```python
# Dependencies
import pandas as pd
import numpy as np
```


```python
# Store filepath in a variable
schools_data = "schools_complete.csv"
students_data = "students_complete.csv"
```


```python
# Read our Data file with the pandas library
schools_data_df = pd.read_csv(schools_data)
```


```python
schools_data_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
  </tbody>
</table>
</div>




```python
#rename "name" column to "school"
schools_data_df = schools_data_df.rename(columns={"name":"school"})

schools_data_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
  </tbody>
</table>
</div>




```python
students_data_df = pd.read_csv(students_data)
```


```python
students_data_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Merge two files on school name
#rename "name" column to "school"
combined_schools_df = pd.merge(schools_data_df, students_data_df, how="outer", on="school")
combined_schools_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>97</td>
      <td>84</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>5</td>
      <td>Bryan Miranda</td>
      <td>M</td>
      <td>9th</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>6</td>
      <td>Sheena Carter</td>
      <td>F</td>
      <td>11th</td>
      <td>82</td>
      <td>80</td>
    </tr>
    <tr>
      <th>7</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>7</td>
      <td>Nicole Baker</td>
      <td>F</td>
      <td>12th</td>
      <td>96</td>
      <td>69</td>
    </tr>
    <tr>
      <th>8</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>8</td>
      <td>Michael Roth</td>
      <td>M</td>
      <td>10th</td>
      <td>95</td>
      <td>87</td>
    </tr>
    <tr>
      <th>9</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>9</td>
      <td>Matthew Greene</td>
      <td>M</td>
      <td>10th</td>
      <td>96</td>
      <td>84</td>
    </tr>
    <tr>
      <th>10</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>10</td>
      <td>Andrew Alexander</td>
      <td>M</td>
      <td>10th</td>
      <td>90</td>
      <td>70</td>
    </tr>
    <tr>
      <th>11</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>11</td>
      <td>Daniel Cooper</td>
      <td>M</td>
      <td>10th</td>
      <td>78</td>
      <td>77</td>
    </tr>
    <tr>
      <th>12</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>12</td>
      <td>Brittney Walker</td>
      <td>F</td>
      <td>9th</td>
      <td>64</td>
      <td>79</td>
    </tr>
    <tr>
      <th>13</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>13</td>
      <td>William Long</td>
      <td>M</td>
      <td>9th</td>
      <td>71</td>
      <td>79</td>
    </tr>
    <tr>
      <th>14</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>14</td>
      <td>Tammy Hebert</td>
      <td>F</td>
      <td>10th</td>
      <td>85</td>
      <td>67</td>
    </tr>
    <tr>
      <th>15</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>15</td>
      <td>Dr. Jordan Carson</td>
      <td>M</td>
      <td>11th</td>
      <td>94</td>
      <td>88</td>
    </tr>
    <tr>
      <th>16</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>16</td>
      <td>Donald Zamora</td>
      <td>M</td>
      <td>9th</td>
      <td>88</td>
      <td>55</td>
    </tr>
    <tr>
      <th>17</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>17</td>
      <td>Kimberly Santiago</td>
      <td>F</td>
      <td>9th</td>
      <td>74</td>
      <td>75</td>
    </tr>
    <tr>
      <th>18</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>18</td>
      <td>Kevin Stevens</td>
      <td>M</td>
      <td>9th</td>
      <td>64</td>
      <td>69</td>
    </tr>
    <tr>
      <th>19</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>19</td>
      <td>Brandi Lyons</td>
      <td>F</td>
      <td>9th</td>
      <td>89</td>
      <td>80</td>
    </tr>
    <tr>
      <th>20</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>20</td>
      <td>Lisa Davis</td>
      <td>F</td>
      <td>10th</td>
      <td>91</td>
      <td>89</td>
    </tr>
    <tr>
      <th>21</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>21</td>
      <td>Kristen Lopez</td>
      <td>F</td>
      <td>10th</td>
      <td>90</td>
      <td>77</td>
    </tr>
    <tr>
      <th>22</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>22</td>
      <td>Kimberly Stewart</td>
      <td>F</td>
      <td>11th</td>
      <td>99</td>
      <td>84</td>
    </tr>
    <tr>
      <th>23</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>23</td>
      <td>Christopher Parker</td>
      <td>M</td>
      <td>9th</td>
      <td>81</td>
      <td>68</td>
    </tr>
    <tr>
      <th>24</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>24</td>
      <td>Chelsea Griffith</td>
      <td>F</td>
      <td>11th</td>
      <td>85</td>
      <td>73</td>
    </tr>
    <tr>
      <th>25</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>25</td>
      <td>Cesar Morris</td>
      <td>M</td>
      <td>9th</td>
      <td>92</td>
      <td>70</td>
    </tr>
    <tr>
      <th>26</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>26</td>
      <td>Melanie Decker</td>
      <td>F</td>
      <td>9th</td>
      <td>63</td>
      <td>85</td>
    </tr>
    <tr>
      <th>27</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>27</td>
      <td>Tracey Oconnor</td>
      <td>F</td>
      <td>10th</td>
      <td>80</td>
      <td>58</td>
    </tr>
    <tr>
      <th>28</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>28</td>
      <td>Kelly James</td>
      <td>F</td>
      <td>11th</td>
      <td>73</td>
      <td>55</td>
    </tr>
    <tr>
      <th>29</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>29</td>
      <td>Nicole Brown</td>
      <td>F</td>
      <td>12th</td>
      <td>90</td>
      <td>88</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>39140</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39140</td>
      <td>Cheyenne Hernandez</td>
      <td>F</td>
      <td>9th</td>
      <td>76</td>
      <td>99</td>
    </tr>
    <tr>
      <th>39141</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39141</td>
      <td>Jonathan Sullivan</td>
      <td>M</td>
      <td>10th</td>
      <td>86</td>
      <td>93</td>
    </tr>
    <tr>
      <th>39142</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39142</td>
      <td>Deborah Higgins DDS</td>
      <td>F</td>
      <td>10th</td>
      <td>96</td>
      <td>83</td>
    </tr>
    <tr>
      <th>39143</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39143</td>
      <td>Steven Jackson</td>
      <td>M</td>
      <td>11th</td>
      <td>71</td>
      <td>93</td>
    </tr>
    <tr>
      <th>39144</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39144</td>
      <td>Cristian Webster</td>
      <td>M</td>
      <td>12th</td>
      <td>77</td>
      <td>87</td>
    </tr>
    <tr>
      <th>39145</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39145</td>
      <td>Audrey Fry</td>
      <td>F</td>
      <td>10th</td>
      <td>94</td>
      <td>74</td>
    </tr>
    <tr>
      <th>39146</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39146</td>
      <td>Michael Carroll</td>
      <td>M</td>
      <td>9th</td>
      <td>69</td>
      <td>95</td>
    </tr>
    <tr>
      <th>39147</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39147</td>
      <td>Raymond Hawkins</td>
      <td>M</td>
      <td>10th</td>
      <td>88</td>
      <td>81</td>
    </tr>
    <tr>
      <th>39148</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39148</td>
      <td>Christopher Wilson</td>
      <td>M</td>
      <td>10th</td>
      <td>89</td>
      <td>89</td>
    </tr>
    <tr>
      <th>39149</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39149</td>
      <td>Glenda Fletcher</td>
      <td>F</td>
      <td>11th</td>
      <td>82</td>
      <td>93</td>
    </tr>
    <tr>
      <th>39150</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39150</td>
      <td>Jennifer Hamilton</td>
      <td>F</td>
      <td>11th</td>
      <td>80</td>
      <td>75</td>
    </tr>
    <tr>
      <th>39151</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39151</td>
      <td>Shannon Williams</td>
      <td>F</td>
      <td>10th</td>
      <td>84</td>
      <td>73</td>
    </tr>
    <tr>
      <th>39152</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39152</td>
      <td>Lori Moore</td>
      <td>F</td>
      <td>9th</td>
      <td>98</td>
      <td>84</td>
    </tr>
    <tr>
      <th>39153</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39153</td>
      <td>William Hubbard</td>
      <td>M</td>
      <td>9th</td>
      <td>80</td>
      <td>75</td>
    </tr>
    <tr>
      <th>39154</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39154</td>
      <td>Bradley Johnson</td>
      <td>M</td>
      <td>12th</td>
      <td>91</td>
      <td>71</td>
    </tr>
    <tr>
      <th>39155</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39155</td>
      <td>John Brooks</td>
      <td>M</td>
      <td>10th</td>
      <td>92</td>
      <td>98</td>
    </tr>
    <tr>
      <th>39156</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39156</td>
      <td>Stephanie Contreras</td>
      <td>F</td>
      <td>11th</td>
      <td>79</td>
      <td>95</td>
    </tr>
    <tr>
      <th>39157</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39157</td>
      <td>Kristen Gonzalez</td>
      <td>F</td>
      <td>9th</td>
      <td>79</td>
      <td>94</td>
    </tr>
    <tr>
      <th>39158</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39158</td>
      <td>Kari Holloway</td>
      <td>F</td>
      <td>10th</td>
      <td>87</td>
      <td>90</td>
    </tr>
    <tr>
      <th>39159</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39159</td>
      <td>Kimberly Cabrera</td>
      <td>F</td>
      <td>11th</td>
      <td>85</td>
      <td>72</td>
    </tr>
    <tr>
      <th>39160</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39160</td>
      <td>Katie Weaver</td>
      <td>F</td>
      <td>11th</td>
      <td>89</td>
      <td>86</td>
    </tr>
    <tr>
      <th>39161</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39161</td>
      <td>April Reyes</td>
      <td>F</td>
      <td>10th</td>
      <td>70</td>
      <td>84</td>
    </tr>
    <tr>
      <th>39162</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39162</td>
      <td>Derek Weeks</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>77</td>
    </tr>
    <tr>
      <th>39163</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39163</td>
      <td>John Reese</td>
      <td>M</td>
      <td>11th</td>
      <td>90</td>
      <td>75</td>
    </tr>
    <tr>
      <th>39164</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39164</td>
      <td>Joseph Anthony</td>
      <td>M</td>
      <td>9th</td>
      <td>97</td>
      <td>76</td>
    </tr>
    <tr>
      <th>39165</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39165</td>
      <td>Donna Howard</td>
      <td>F</td>
      <td>12th</td>
      <td>99</td>
      <td>90</td>
    </tr>
    <tr>
      <th>39166</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39166</td>
      <td>Dawn Bell</td>
      <td>F</td>
      <td>10th</td>
      <td>95</td>
      <td>70</td>
    </tr>
    <tr>
      <th>39167</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39167</td>
      <td>Rebecca Tanner</td>
      <td>F</td>
      <td>9th</td>
      <td>73</td>
      <td>84</td>
    </tr>
    <tr>
      <th>39168</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39168</td>
      <td>Desiree Kidd</td>
      <td>F</td>
      <td>10th</td>
      <td>99</td>
      <td>90</td>
    </tr>
    <tr>
      <th>39169</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39169</td>
      <td>Carolyn Jackson</td>
      <td>F</td>
      <td>11th</td>
      <td>95</td>
      <td>75</td>
    </tr>
  </tbody>
</table>
<p>39170 rows × 11 columns</p>
</div>




```python
combined_schools_df.describe()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>size</th>
      <th>budget</th>
      <th>Student ID</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>39170.000000</td>
      <td>39170.000000</td>
      <td>3.917000e+04</td>
      <td>39170.000000</td>
      <td>39170.00000</td>
      <td>39170.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>6.978172</td>
      <td>3332.957110</td>
      <td>2.117241e+06</td>
      <td>19584.500000</td>
      <td>81.87784</td>
      <td>78.985371</td>
    </tr>
    <tr>
      <th>std</th>
      <td>4.444329</td>
      <td>1323.914069</td>
      <td>8.749987e+05</td>
      <td>11307.549359</td>
      <td>10.23958</td>
      <td>12.309968</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000000</td>
      <td>427.000000</td>
      <td>2.480870e+05</td>
      <td>0.000000</td>
      <td>63.00000</td>
      <td>55.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>3.000000</td>
      <td>1858.000000</td>
      <td>1.081356e+06</td>
      <td>9792.250000</td>
      <td>73.00000</td>
      <td>69.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>7.000000</td>
      <td>2949.000000</td>
      <td>1.910635e+06</td>
      <td>19584.500000</td>
      <td>82.00000</td>
      <td>79.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>11.000000</td>
      <td>4635.000000</td>
      <td>3.022020e+06</td>
      <td>29376.750000</td>
      <td>91.00000</td>
      <td>89.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>14.000000</td>
      <td>4976.000000</td>
      <td>3.124928e+06</td>
      <td>39169.000000</td>
      <td>99.00000</td>
      <td>99.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
#unique_schools = combined_schools_df["school"].unique()
#unique

#total_schools = 15
total_schools = schools_data_df["school"].count()
total_schools

```




    15




```python
#total students = 39170
total_students = students_data_df["name"].count()
total_students
```




    39170




```python
#total_budget = 24649428
total_budget = schools_data_df["budget"].sum()
total_budget
```




    24649428




```python
#total math score = 3093857
total_math = combined_schools_df["math_score"].sum()
total_math
```




    3093857




```python
#total reading score = 3207155 
total_reading = combined_schools_df["reading_score"].sum()
total_reading
```




    3207155




```python
#Find average of math = 78.985371457748272
math_average = total_math / total_students
math_average

```




    78.985371457748272




```python
#reading_average = 81.877840183814143
reading_average = total_reading / total_students
reading_average
```




    81.877840183814143




```python
# Extract only students who are passing math(above a "C":70)
passing_students_math_df = combined_schools_df.loc[(combined_schools_df["math_score"] > 70)]
passing_students_math_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>97</td>
      <td>84</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>5</td>
      <td>Bryan Miranda</td>
      <td>M</td>
      <td>9th</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>6</td>
      <td>Sheena Carter</td>
      <td>F</td>
      <td>11th</td>
      <td>82</td>
      <td>80</td>
    </tr>
    <tr>
      <th>8</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>8</td>
      <td>Michael Roth</td>
      <td>M</td>
      <td>10th</td>
      <td>95</td>
      <td>87</td>
    </tr>
    <tr>
      <th>9</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>9</td>
      <td>Matthew Greene</td>
      <td>M</td>
      <td>10th</td>
      <td>96</td>
      <td>84</td>
    </tr>
    <tr>
      <th>11</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>11</td>
      <td>Daniel Cooper</td>
      <td>M</td>
      <td>10th</td>
      <td>78</td>
      <td>77</td>
    </tr>
    <tr>
      <th>12</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>12</td>
      <td>Brittney Walker</td>
      <td>F</td>
      <td>9th</td>
      <td>64</td>
      <td>79</td>
    </tr>
    <tr>
      <th>13</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>13</td>
      <td>William Long</td>
      <td>M</td>
      <td>9th</td>
      <td>71</td>
      <td>79</td>
    </tr>
    <tr>
      <th>15</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>15</td>
      <td>Dr. Jordan Carson</td>
      <td>M</td>
      <td>11th</td>
      <td>94</td>
      <td>88</td>
    </tr>
    <tr>
      <th>17</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>17</td>
      <td>Kimberly Santiago</td>
      <td>F</td>
      <td>9th</td>
      <td>74</td>
      <td>75</td>
    </tr>
    <tr>
      <th>19</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>19</td>
      <td>Brandi Lyons</td>
      <td>F</td>
      <td>9th</td>
      <td>89</td>
      <td>80</td>
    </tr>
    <tr>
      <th>20</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>20</td>
      <td>Lisa Davis</td>
      <td>F</td>
      <td>10th</td>
      <td>91</td>
      <td>89</td>
    </tr>
    <tr>
      <th>21</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>21</td>
      <td>Kristen Lopez</td>
      <td>F</td>
      <td>10th</td>
      <td>90</td>
      <td>77</td>
    </tr>
    <tr>
      <th>22</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>22</td>
      <td>Kimberly Stewart</td>
      <td>F</td>
      <td>11th</td>
      <td>99</td>
      <td>84</td>
    </tr>
    <tr>
      <th>24</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>24</td>
      <td>Chelsea Griffith</td>
      <td>F</td>
      <td>11th</td>
      <td>85</td>
      <td>73</td>
    </tr>
    <tr>
      <th>26</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>26</td>
      <td>Melanie Decker</td>
      <td>F</td>
      <td>9th</td>
      <td>63</td>
      <td>85</td>
    </tr>
    <tr>
      <th>29</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>29</td>
      <td>Nicole Brown</td>
      <td>F</td>
      <td>12th</td>
      <td>90</td>
      <td>88</td>
    </tr>
    <tr>
      <th>30</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>30</td>
      <td>Bobby Harris</td>
      <td>M</td>
      <td>9th</td>
      <td>94</td>
      <td>99</td>
    </tr>
    <tr>
      <th>32</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>32</td>
      <td>Candace Phelps</td>
      <td>F</td>
      <td>11th</td>
      <td>93</td>
      <td>90</td>
    </tr>
    <tr>
      <th>34</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>34</td>
      <td>Steven Green</td>
      <td>M</td>
      <td>11th</td>
      <td>65</td>
      <td>74</td>
    </tr>
    <tr>
      <th>36</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>36</td>
      <td>Kevin Bailey</td>
      <td>M</td>
      <td>10th</td>
      <td>76</td>
      <td>76</td>
    </tr>
    <tr>
      <th>38</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>38</td>
      <td>Kimberly Mercado</td>
      <td>F</td>
      <td>12th</td>
      <td>73</td>
      <td>77</td>
    </tr>
    <tr>
      <th>41</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>41</td>
      <td>Jennifer Parks</td>
      <td>F</td>
      <td>11th</td>
      <td>85</td>
      <td>95</td>
    </tr>
    <tr>
      <th>42</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>42</td>
      <td>John Carlson</td>
      <td>M</td>
      <td>9th</td>
      <td>65</td>
      <td>89</td>
    </tr>
    <tr>
      <th>43</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>43</td>
      <td>Megan Roberts</td>
      <td>F</td>
      <td>9th</td>
      <td>66</td>
      <td>90</td>
    </tr>
    <tr>
      <th>45</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>45</td>
      <td>Heidi Jackson</td>
      <td>F</td>
      <td>11th</td>
      <td>64</td>
      <td>93</td>
    </tr>
    <tr>
      <th>47</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>47</td>
      <td>Ellen Brown</td>
      <td>F</td>
      <td>11th</td>
      <td>77</td>
      <td>81</td>
    </tr>
    <tr>
      <th>49</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>49</td>
      <td>Natalie Mitchell</td>
      <td>F</td>
      <td>10th</td>
      <td>73</td>
      <td>93</td>
    </tr>
    <tr>
      <th>50</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>50</td>
      <td>Tiffany Gutierrez</td>
      <td>F</td>
      <td>10th</td>
      <td>82</td>
      <td>95</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>39139</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39139</td>
      <td>Catherine Lee</td>
      <td>F</td>
      <td>9th</td>
      <td>83</td>
      <td>81</td>
    </tr>
    <tr>
      <th>39140</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39140</td>
      <td>Cheyenne Hernandez</td>
      <td>F</td>
      <td>9th</td>
      <td>76</td>
      <td>99</td>
    </tr>
    <tr>
      <th>39141</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39141</td>
      <td>Jonathan Sullivan</td>
      <td>M</td>
      <td>10th</td>
      <td>86</td>
      <td>93</td>
    </tr>
    <tr>
      <th>39142</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39142</td>
      <td>Deborah Higgins DDS</td>
      <td>F</td>
      <td>10th</td>
      <td>96</td>
      <td>83</td>
    </tr>
    <tr>
      <th>39143</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39143</td>
      <td>Steven Jackson</td>
      <td>M</td>
      <td>11th</td>
      <td>71</td>
      <td>93</td>
    </tr>
    <tr>
      <th>39144</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39144</td>
      <td>Cristian Webster</td>
      <td>M</td>
      <td>12th</td>
      <td>77</td>
      <td>87</td>
    </tr>
    <tr>
      <th>39145</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39145</td>
      <td>Audrey Fry</td>
      <td>F</td>
      <td>10th</td>
      <td>94</td>
      <td>74</td>
    </tr>
    <tr>
      <th>39146</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39146</td>
      <td>Michael Carroll</td>
      <td>M</td>
      <td>9th</td>
      <td>69</td>
      <td>95</td>
    </tr>
    <tr>
      <th>39147</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39147</td>
      <td>Raymond Hawkins</td>
      <td>M</td>
      <td>10th</td>
      <td>88</td>
      <td>81</td>
    </tr>
    <tr>
      <th>39148</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39148</td>
      <td>Christopher Wilson</td>
      <td>M</td>
      <td>10th</td>
      <td>89</td>
      <td>89</td>
    </tr>
    <tr>
      <th>39149</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39149</td>
      <td>Glenda Fletcher</td>
      <td>F</td>
      <td>11th</td>
      <td>82</td>
      <td>93</td>
    </tr>
    <tr>
      <th>39150</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39150</td>
      <td>Jennifer Hamilton</td>
      <td>F</td>
      <td>11th</td>
      <td>80</td>
      <td>75</td>
    </tr>
    <tr>
      <th>39151</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39151</td>
      <td>Shannon Williams</td>
      <td>F</td>
      <td>10th</td>
      <td>84</td>
      <td>73</td>
    </tr>
    <tr>
      <th>39152</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39152</td>
      <td>Lori Moore</td>
      <td>F</td>
      <td>9th</td>
      <td>98</td>
      <td>84</td>
    </tr>
    <tr>
      <th>39153</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39153</td>
      <td>William Hubbard</td>
      <td>M</td>
      <td>9th</td>
      <td>80</td>
      <td>75</td>
    </tr>
    <tr>
      <th>39154</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39154</td>
      <td>Bradley Johnson</td>
      <td>M</td>
      <td>12th</td>
      <td>91</td>
      <td>71</td>
    </tr>
    <tr>
      <th>39155</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39155</td>
      <td>John Brooks</td>
      <td>M</td>
      <td>10th</td>
      <td>92</td>
      <td>98</td>
    </tr>
    <tr>
      <th>39156</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39156</td>
      <td>Stephanie Contreras</td>
      <td>F</td>
      <td>11th</td>
      <td>79</td>
      <td>95</td>
    </tr>
    <tr>
      <th>39157</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39157</td>
      <td>Kristen Gonzalez</td>
      <td>F</td>
      <td>9th</td>
      <td>79</td>
      <td>94</td>
    </tr>
    <tr>
      <th>39158</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39158</td>
      <td>Kari Holloway</td>
      <td>F</td>
      <td>10th</td>
      <td>87</td>
      <td>90</td>
    </tr>
    <tr>
      <th>39159</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39159</td>
      <td>Kimberly Cabrera</td>
      <td>F</td>
      <td>11th</td>
      <td>85</td>
      <td>72</td>
    </tr>
    <tr>
      <th>39160</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39160</td>
      <td>Katie Weaver</td>
      <td>F</td>
      <td>11th</td>
      <td>89</td>
      <td>86</td>
    </tr>
    <tr>
      <th>39161</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39161</td>
      <td>April Reyes</td>
      <td>F</td>
      <td>10th</td>
      <td>70</td>
      <td>84</td>
    </tr>
    <tr>
      <th>39162</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39162</td>
      <td>Derek Weeks</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>77</td>
    </tr>
    <tr>
      <th>39163</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39163</td>
      <td>John Reese</td>
      <td>M</td>
      <td>11th</td>
      <td>90</td>
      <td>75</td>
    </tr>
    <tr>
      <th>39164</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39164</td>
      <td>Joseph Anthony</td>
      <td>M</td>
      <td>9th</td>
      <td>97</td>
      <td>76</td>
    </tr>
    <tr>
      <th>39165</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39165</td>
      <td>Donna Howard</td>
      <td>F</td>
      <td>12th</td>
      <td>99</td>
      <td>90</td>
    </tr>
    <tr>
      <th>39167</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39167</td>
      <td>Rebecca Tanner</td>
      <td>F</td>
      <td>9th</td>
      <td>73</td>
      <td>84</td>
    </tr>
    <tr>
      <th>39168</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39168</td>
      <td>Desiree Kidd</td>
      <td>F</td>
      <td>10th</td>
      <td>99</td>
      <td>90</td>
    </tr>
    <tr>
      <th>39169</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39169</td>
      <td>Carolyn Jackson</td>
      <td>F</td>
      <td>11th</td>
      <td>95</td>
      <td>75</td>
    </tr>
  </tbody>
</table>
<p>28356 rows × 11 columns</p>
</div>




```python
#total_math_passing = 2409941
total_math_passing = passing_students_math_df["math_score"].sum()
total_math_passing 
```




    2409941




```python
#count of passing math students = 28356
total_students_passing = passing_students_math_df["name"].count()
total_students_passing
```




    28356




```python
#percentage passing math = 72.392136839417915
passing_math_percent = (total_students_passing / total_students) * 100
passing_math_percent
```




    72.392136839417915




```python
# Extract only students who are passing reading(above a "C":70)
passing_students_reading_df = combined_schools_df.loc[(combined_schools_df["reading_score"] > 70)]
passing_students_reading_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>97</td>
      <td>84</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>5</td>
      <td>Bryan Miranda</td>
      <td>M</td>
      <td>9th</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>6</td>
      <td>Sheena Carter</td>
      <td>F</td>
      <td>11th</td>
      <td>82</td>
      <td>80</td>
    </tr>
    <tr>
      <th>7</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>7</td>
      <td>Nicole Baker</td>
      <td>F</td>
      <td>12th</td>
      <td>96</td>
      <td>69</td>
    </tr>
    <tr>
      <th>8</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>8</td>
      <td>Michael Roth</td>
      <td>M</td>
      <td>10th</td>
      <td>95</td>
      <td>87</td>
    </tr>
    <tr>
      <th>9</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>9</td>
      <td>Matthew Greene</td>
      <td>M</td>
      <td>10th</td>
      <td>96</td>
      <td>84</td>
    </tr>
    <tr>
      <th>10</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>10</td>
      <td>Andrew Alexander</td>
      <td>M</td>
      <td>10th</td>
      <td>90</td>
      <td>70</td>
    </tr>
    <tr>
      <th>11</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>11</td>
      <td>Daniel Cooper</td>
      <td>M</td>
      <td>10th</td>
      <td>78</td>
      <td>77</td>
    </tr>
    <tr>
      <th>13</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>13</td>
      <td>William Long</td>
      <td>M</td>
      <td>9th</td>
      <td>71</td>
      <td>79</td>
    </tr>
    <tr>
      <th>14</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>14</td>
      <td>Tammy Hebert</td>
      <td>F</td>
      <td>10th</td>
      <td>85</td>
      <td>67</td>
    </tr>
    <tr>
      <th>15</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>15</td>
      <td>Dr. Jordan Carson</td>
      <td>M</td>
      <td>11th</td>
      <td>94</td>
      <td>88</td>
    </tr>
    <tr>
      <th>16</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>16</td>
      <td>Donald Zamora</td>
      <td>M</td>
      <td>9th</td>
      <td>88</td>
      <td>55</td>
    </tr>
    <tr>
      <th>17</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>17</td>
      <td>Kimberly Santiago</td>
      <td>F</td>
      <td>9th</td>
      <td>74</td>
      <td>75</td>
    </tr>
    <tr>
      <th>19</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>19</td>
      <td>Brandi Lyons</td>
      <td>F</td>
      <td>9th</td>
      <td>89</td>
      <td>80</td>
    </tr>
    <tr>
      <th>20</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>20</td>
      <td>Lisa Davis</td>
      <td>F</td>
      <td>10th</td>
      <td>91</td>
      <td>89</td>
    </tr>
    <tr>
      <th>21</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>21</td>
      <td>Kristen Lopez</td>
      <td>F</td>
      <td>10th</td>
      <td>90</td>
      <td>77</td>
    </tr>
    <tr>
      <th>22</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>22</td>
      <td>Kimberly Stewart</td>
      <td>F</td>
      <td>11th</td>
      <td>99</td>
      <td>84</td>
    </tr>
    <tr>
      <th>23</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>23</td>
      <td>Christopher Parker</td>
      <td>M</td>
      <td>9th</td>
      <td>81</td>
      <td>68</td>
    </tr>
    <tr>
      <th>24</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>24</td>
      <td>Chelsea Griffith</td>
      <td>F</td>
      <td>11th</td>
      <td>85</td>
      <td>73</td>
    </tr>
    <tr>
      <th>25</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>25</td>
      <td>Cesar Morris</td>
      <td>M</td>
      <td>9th</td>
      <td>92</td>
      <td>70</td>
    </tr>
    <tr>
      <th>27</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>27</td>
      <td>Tracey Oconnor</td>
      <td>F</td>
      <td>10th</td>
      <td>80</td>
      <td>58</td>
    </tr>
    <tr>
      <th>28</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>28</td>
      <td>Kelly James</td>
      <td>F</td>
      <td>11th</td>
      <td>73</td>
      <td>55</td>
    </tr>
    <tr>
      <th>29</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>29</td>
      <td>Nicole Brown</td>
      <td>F</td>
      <td>12th</td>
      <td>90</td>
      <td>88</td>
    </tr>
    <tr>
      <th>30</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>30</td>
      <td>Bobby Harris</td>
      <td>M</td>
      <td>9th</td>
      <td>94</td>
      <td>99</td>
    </tr>
    <tr>
      <th>31</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>31</td>
      <td>Brian Fernandez</td>
      <td>M</td>
      <td>10th</td>
      <td>97</td>
      <td>65</td>
    </tr>
    <tr>
      <th>32</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>32</td>
      <td>Candace Phelps</td>
      <td>F</td>
      <td>11th</td>
      <td>93</td>
      <td>90</td>
    </tr>
    <tr>
      <th>33</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>33</td>
      <td>Amy Gonzalez</td>
      <td>F</td>
      <td>12th</td>
      <td>95</td>
      <td>68</td>
    </tr>
    <tr>
      <th>35</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>35</td>
      <td>Benjamin Carlson</td>
      <td>M</td>
      <td>10th</td>
      <td>99</td>
      <td>61</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>39138</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39138</td>
      <td>Monica Hampton</td>
      <td>F</td>
      <td>9th</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <th>39139</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39139</td>
      <td>Catherine Lee</td>
      <td>F</td>
      <td>9th</td>
      <td>83</td>
      <td>81</td>
    </tr>
    <tr>
      <th>39140</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39140</td>
      <td>Cheyenne Hernandez</td>
      <td>F</td>
      <td>9th</td>
      <td>76</td>
      <td>99</td>
    </tr>
    <tr>
      <th>39141</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39141</td>
      <td>Jonathan Sullivan</td>
      <td>M</td>
      <td>10th</td>
      <td>86</td>
      <td>93</td>
    </tr>
    <tr>
      <th>39142</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39142</td>
      <td>Deborah Higgins DDS</td>
      <td>F</td>
      <td>10th</td>
      <td>96</td>
      <td>83</td>
    </tr>
    <tr>
      <th>39143</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39143</td>
      <td>Steven Jackson</td>
      <td>M</td>
      <td>11th</td>
      <td>71</td>
      <td>93</td>
    </tr>
    <tr>
      <th>39144</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39144</td>
      <td>Cristian Webster</td>
      <td>M</td>
      <td>12th</td>
      <td>77</td>
      <td>87</td>
    </tr>
    <tr>
      <th>39145</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39145</td>
      <td>Audrey Fry</td>
      <td>F</td>
      <td>10th</td>
      <td>94</td>
      <td>74</td>
    </tr>
    <tr>
      <th>39147</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39147</td>
      <td>Raymond Hawkins</td>
      <td>M</td>
      <td>10th</td>
      <td>88</td>
      <td>81</td>
    </tr>
    <tr>
      <th>39148</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39148</td>
      <td>Christopher Wilson</td>
      <td>M</td>
      <td>10th</td>
      <td>89</td>
      <td>89</td>
    </tr>
    <tr>
      <th>39149</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39149</td>
      <td>Glenda Fletcher</td>
      <td>F</td>
      <td>11th</td>
      <td>82</td>
      <td>93</td>
    </tr>
    <tr>
      <th>39150</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39150</td>
      <td>Jennifer Hamilton</td>
      <td>F</td>
      <td>11th</td>
      <td>80</td>
      <td>75</td>
    </tr>
    <tr>
      <th>39151</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39151</td>
      <td>Shannon Williams</td>
      <td>F</td>
      <td>10th</td>
      <td>84</td>
      <td>73</td>
    </tr>
    <tr>
      <th>39152</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39152</td>
      <td>Lori Moore</td>
      <td>F</td>
      <td>9th</td>
      <td>98</td>
      <td>84</td>
    </tr>
    <tr>
      <th>39153</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39153</td>
      <td>William Hubbard</td>
      <td>M</td>
      <td>9th</td>
      <td>80</td>
      <td>75</td>
    </tr>
    <tr>
      <th>39154</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39154</td>
      <td>Bradley Johnson</td>
      <td>M</td>
      <td>12th</td>
      <td>91</td>
      <td>71</td>
    </tr>
    <tr>
      <th>39155</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39155</td>
      <td>John Brooks</td>
      <td>M</td>
      <td>10th</td>
      <td>92</td>
      <td>98</td>
    </tr>
    <tr>
      <th>39156</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39156</td>
      <td>Stephanie Contreras</td>
      <td>F</td>
      <td>11th</td>
      <td>79</td>
      <td>95</td>
    </tr>
    <tr>
      <th>39157</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39157</td>
      <td>Kristen Gonzalez</td>
      <td>F</td>
      <td>9th</td>
      <td>79</td>
      <td>94</td>
    </tr>
    <tr>
      <th>39158</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39158</td>
      <td>Kari Holloway</td>
      <td>F</td>
      <td>10th</td>
      <td>87</td>
      <td>90</td>
    </tr>
    <tr>
      <th>39159</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39159</td>
      <td>Kimberly Cabrera</td>
      <td>F</td>
      <td>11th</td>
      <td>85</td>
      <td>72</td>
    </tr>
    <tr>
      <th>39160</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39160</td>
      <td>Katie Weaver</td>
      <td>F</td>
      <td>11th</td>
      <td>89</td>
      <td>86</td>
    </tr>
    <tr>
      <th>39162</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39162</td>
      <td>Derek Weeks</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>77</td>
    </tr>
    <tr>
      <th>39163</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39163</td>
      <td>John Reese</td>
      <td>M</td>
      <td>11th</td>
      <td>90</td>
      <td>75</td>
    </tr>
    <tr>
      <th>39164</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39164</td>
      <td>Joseph Anthony</td>
      <td>M</td>
      <td>9th</td>
      <td>97</td>
      <td>76</td>
    </tr>
    <tr>
      <th>39165</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39165</td>
      <td>Donna Howard</td>
      <td>F</td>
      <td>12th</td>
      <td>99</td>
      <td>90</td>
    </tr>
    <tr>
      <th>39166</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39166</td>
      <td>Dawn Bell</td>
      <td>F</td>
      <td>10th</td>
      <td>95</td>
      <td>70</td>
    </tr>
    <tr>
      <th>39167</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39167</td>
      <td>Rebecca Tanner</td>
      <td>F</td>
      <td>9th</td>
      <td>73</td>
      <td>84</td>
    </tr>
    <tr>
      <th>39168</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39168</td>
      <td>Desiree Kidd</td>
      <td>F</td>
      <td>10th</td>
      <td>99</td>
      <td>90</td>
    </tr>
    <tr>
      <th>39169</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39169</td>
      <td>Carolyn Jackson</td>
      <td>F</td>
      <td>11th</td>
      <td>95</td>
      <td>75</td>
    </tr>
  </tbody>
</table>
<p>32500 rows × 11 columns</p>
</div>




```python
#total reading passing score = 2761446
total_reading_passing = passing_students_reading_df["reading_score"].sum()
total_reading_passing
```




    2761446




```python
#count of passing reading students = 32500
total_students_passing_reading = passing_students_reading_df["name"].count()
total_students_passing_reading
```




    32500




```python
#percentage passing reading = 82.971661986213945
passing_reading_percent = (total_students_passing_reading / total_students) * 100
passing_reading_percent
```




    82.971661986213945




```python
average_passing = (passing_reading_percent + passing_math_percent) / 2
average_passing
```




    77.681899412815937




```python
# Creating a summary DataFrame using calculated values; transpose to switch columns & index
district_summary_df = pd.DataFrame({"Total Schools":[total_schools],
                          "Total Students":[total_students],
                          "Total Budget":str(total_budget)+" dollars",
                          "Average Math Score":[math_average],
                          "Average Reading Score":[reading_average],
                          "Percent Passing Math":str(passing_math_percent)+"%",
                          "Percent Passing Reading":str(passing_reading_percent)+"%",
                          "Overall Passing Rate":str(average_passing)+"%"})
district_summary_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>Overall Passing Rate</th>
      <th>Percent Passing Math</th>
      <th>Percent Passing Reading</th>
      <th>Total Budget</th>
      <th>Total Schools</th>
      <th>Total Students</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>78.985371</td>
      <td>81.87784</td>
      <td>77.6818994128%</td>
      <td>72.3921368394%</td>
      <td>82.9716619862%</td>
      <td>24649428 dollars</td>
      <td>15</td>
      <td>39170</td>
    </tr>
  </tbody>
</table>
</div>




```python
school_summary_df = combined_schools_df.groupby('name')
school_summary_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>97</td>
      <td>84</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>5</td>
      <td>Bryan Miranda</td>
      <td>M</td>
      <td>9th</td>
      <td>94</td>
      <td>94</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>6</td>
      <td>Sheena Carter</td>
      <td>F</td>
      <td>11th</td>
      <td>82</td>
      <td>80</td>
    </tr>
    <tr>
      <th>7</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>7</td>
      <td>Nicole Baker</td>
      <td>F</td>
      <td>12th</td>
      <td>96</td>
      <td>69</td>
    </tr>
    <tr>
      <th>8</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>8</td>
      <td>Michael Roth</td>
      <td>M</td>
      <td>10th</td>
      <td>95</td>
      <td>87</td>
    </tr>
    <tr>
      <th>9</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>9</td>
      <td>Matthew Greene</td>
      <td>M</td>
      <td>10th</td>
      <td>96</td>
      <td>84</td>
    </tr>
    <tr>
      <th>10</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>10</td>
      <td>Andrew Alexander</td>
      <td>M</td>
      <td>10th</td>
      <td>90</td>
      <td>70</td>
    </tr>
    <tr>
      <th>11</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>11</td>
      <td>Daniel Cooper</td>
      <td>M</td>
      <td>10th</td>
      <td>78</td>
      <td>77</td>
    </tr>
    <tr>
      <th>12</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>12</td>
      <td>Brittney Walker</td>
      <td>F</td>
      <td>9th</td>
      <td>64</td>
      <td>79</td>
    </tr>
    <tr>
      <th>13</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>13</td>
      <td>William Long</td>
      <td>M</td>
      <td>9th</td>
      <td>71</td>
      <td>79</td>
    </tr>
    <tr>
      <th>14</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>14</td>
      <td>Tammy Hebert</td>
      <td>F</td>
      <td>10th</td>
      <td>85</td>
      <td>67</td>
    </tr>
    <tr>
      <th>15</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>15</td>
      <td>Dr. Jordan Carson</td>
      <td>M</td>
      <td>11th</td>
      <td>94</td>
      <td>88</td>
    </tr>
    <tr>
      <th>16</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>16</td>
      <td>Donald Zamora</td>
      <td>M</td>
      <td>9th</td>
      <td>88</td>
      <td>55</td>
    </tr>
    <tr>
      <th>17</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>17</td>
      <td>Kimberly Santiago</td>
      <td>F</td>
      <td>9th</td>
      <td>74</td>
      <td>75</td>
    </tr>
    <tr>
      <th>18</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>18</td>
      <td>Kevin Stevens</td>
      <td>M</td>
      <td>9th</td>
      <td>64</td>
      <td>69</td>
    </tr>
    <tr>
      <th>19</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>19</td>
      <td>Brandi Lyons</td>
      <td>F</td>
      <td>9th</td>
      <td>89</td>
      <td>80</td>
    </tr>
    <tr>
      <th>20</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>20</td>
      <td>Lisa Davis</td>
      <td>F</td>
      <td>10th</td>
      <td>91</td>
      <td>89</td>
    </tr>
    <tr>
      <th>21</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>21</td>
      <td>Kristen Lopez</td>
      <td>F</td>
      <td>10th</td>
      <td>90</td>
      <td>77</td>
    </tr>
    <tr>
      <th>22</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>22</td>
      <td>Kimberly Stewart</td>
      <td>F</td>
      <td>11th</td>
      <td>99</td>
      <td>84</td>
    </tr>
    <tr>
      <th>23</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>23</td>
      <td>Christopher Parker</td>
      <td>M</td>
      <td>9th</td>
      <td>81</td>
      <td>68</td>
    </tr>
    <tr>
      <th>24</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>24</td>
      <td>Chelsea Griffith</td>
      <td>F</td>
      <td>11th</td>
      <td>85</td>
      <td>73</td>
    </tr>
    <tr>
      <th>25</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>25</td>
      <td>Cesar Morris</td>
      <td>M</td>
      <td>9th</td>
      <td>92</td>
      <td>70</td>
    </tr>
    <tr>
      <th>26</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>26</td>
      <td>Melanie Decker</td>
      <td>F</td>
      <td>9th</td>
      <td>63</td>
      <td>85</td>
    </tr>
    <tr>
      <th>27</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>27</td>
      <td>Tracey Oconnor</td>
      <td>F</td>
      <td>10th</td>
      <td>80</td>
      <td>58</td>
    </tr>
    <tr>
      <th>28</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>28</td>
      <td>Kelly James</td>
      <td>F</td>
      <td>11th</td>
      <td>73</td>
      <td>55</td>
    </tr>
    <tr>
      <th>29</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>29</td>
      <td>Nicole Brown</td>
      <td>F</td>
      <td>12th</td>
      <td>90</td>
      <td>88</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>39140</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39140</td>
      <td>Cheyenne Hernandez</td>
      <td>F</td>
      <td>9th</td>
      <td>76</td>
      <td>99</td>
    </tr>
    <tr>
      <th>39141</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39141</td>
      <td>Jonathan Sullivan</td>
      <td>M</td>
      <td>10th</td>
      <td>86</td>
      <td>93</td>
    </tr>
    <tr>
      <th>39142</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39142</td>
      <td>Deborah Higgins DDS</td>
      <td>F</td>
      <td>10th</td>
      <td>96</td>
      <td>83</td>
    </tr>
    <tr>
      <th>39143</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39143</td>
      <td>Steven Jackson</td>
      <td>M</td>
      <td>11th</td>
      <td>71</td>
      <td>93</td>
    </tr>
    <tr>
      <th>39144</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39144</td>
      <td>Cristian Webster</td>
      <td>M</td>
      <td>12th</td>
      <td>77</td>
      <td>87</td>
    </tr>
    <tr>
      <th>39145</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39145</td>
      <td>Audrey Fry</td>
      <td>F</td>
      <td>10th</td>
      <td>94</td>
      <td>74</td>
    </tr>
    <tr>
      <th>39146</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39146</td>
      <td>Michael Carroll</td>
      <td>M</td>
      <td>9th</td>
      <td>69</td>
      <td>95</td>
    </tr>
    <tr>
      <th>39147</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39147</td>
      <td>Raymond Hawkins</td>
      <td>M</td>
      <td>10th</td>
      <td>88</td>
      <td>81</td>
    </tr>
    <tr>
      <th>39148</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39148</td>
      <td>Christopher Wilson</td>
      <td>M</td>
      <td>10th</td>
      <td>89</td>
      <td>89</td>
    </tr>
    <tr>
      <th>39149</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39149</td>
      <td>Glenda Fletcher</td>
      <td>F</td>
      <td>11th</td>
      <td>82</td>
      <td>93</td>
    </tr>
    <tr>
      <th>39150</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39150</td>
      <td>Jennifer Hamilton</td>
      <td>F</td>
      <td>11th</td>
      <td>80</td>
      <td>75</td>
    </tr>
    <tr>
      <th>39151</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39151</td>
      <td>Shannon Williams</td>
      <td>F</td>
      <td>10th</td>
      <td>84</td>
      <td>73</td>
    </tr>
    <tr>
      <th>39152</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39152</td>
      <td>Lori Moore</td>
      <td>F</td>
      <td>9th</td>
      <td>98</td>
      <td>84</td>
    </tr>
    <tr>
      <th>39153</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39153</td>
      <td>William Hubbard</td>
      <td>M</td>
      <td>9th</td>
      <td>80</td>
      <td>75</td>
    </tr>
    <tr>
      <th>39154</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39154</td>
      <td>Bradley Johnson</td>
      <td>M</td>
      <td>12th</td>
      <td>91</td>
      <td>71</td>
    </tr>
    <tr>
      <th>39155</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39155</td>
      <td>John Brooks</td>
      <td>M</td>
      <td>10th</td>
      <td>92</td>
      <td>98</td>
    </tr>
    <tr>
      <th>39156</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39156</td>
      <td>Stephanie Contreras</td>
      <td>F</td>
      <td>11th</td>
      <td>79</td>
      <td>95</td>
    </tr>
    <tr>
      <th>39157</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39157</td>
      <td>Kristen Gonzalez</td>
      <td>F</td>
      <td>9th</td>
      <td>79</td>
      <td>94</td>
    </tr>
    <tr>
      <th>39158</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39158</td>
      <td>Kari Holloway</td>
      <td>F</td>
      <td>10th</td>
      <td>87</td>
      <td>90</td>
    </tr>
    <tr>
      <th>39159</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39159</td>
      <td>Kimberly Cabrera</td>
      <td>F</td>
      <td>11th</td>
      <td>85</td>
      <td>72</td>
    </tr>
    <tr>
      <th>39160</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39160</td>
      <td>Katie Weaver</td>
      <td>F</td>
      <td>11th</td>
      <td>89</td>
      <td>86</td>
    </tr>
    <tr>
      <th>39161</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39161</td>
      <td>April Reyes</td>
      <td>F</td>
      <td>10th</td>
      <td>70</td>
      <td>84</td>
    </tr>
    <tr>
      <th>39162</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39162</td>
      <td>Derek Weeks</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>77</td>
    </tr>
    <tr>
      <th>39163</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39163</td>
      <td>John Reese</td>
      <td>M</td>
      <td>11th</td>
      <td>90</td>
      <td>75</td>
    </tr>
    <tr>
      <th>39164</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39164</td>
      <td>Joseph Anthony</td>
      <td>M</td>
      <td>9th</td>
      <td>97</td>
      <td>76</td>
    </tr>
    <tr>
      <th>39165</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39165</td>
      <td>Donna Howard</td>
      <td>F</td>
      <td>12th</td>
      <td>99</td>
      <td>90</td>
    </tr>
    <tr>
      <th>39166</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39166</td>
      <td>Dawn Bell</td>
      <td>F</td>
      <td>10th</td>
      <td>95</td>
      <td>70</td>
    </tr>
    <tr>
      <th>39167</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39167</td>
      <td>Rebecca Tanner</td>
      <td>F</td>
      <td>9th</td>
      <td>73</td>
      <td>84</td>
    </tr>
    <tr>
      <th>39168</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39168</td>
      <td>Desiree Kidd</td>
      <td>F</td>
      <td>10th</td>
      <td>99</td>
      <td>90</td>
    </tr>
    <tr>
      <th>39169</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>39169</td>
      <td>Carolyn Jackson</td>
      <td>F</td>
      <td>11th</td>
      <td>95</td>
      <td>75</td>
    </tr>
  </tbody>
</table>
<p>38806 rows × 11 columns</p>
</div>




```python
# Group the data frame by month and item and extract a number of stats from each group
combined_schools_df.groupby(['school']).agg({'school',
                                             'type',
                                             'name': ('name'.count),      
                                             'budget'
                                             'budget': ('budget' / len('name'))
                                             'reading_score': ('reading_score' / len('reading_score'))}) 
```


```python
#rename columns
renamed_combined_schools_df = combined_schools_df.rename(columns={"":"", "":""})
renamed_combined_schools_df.head()
```


```python
#add budget_per_student variable = 629.29354097523617
budget_per_student = total_budget / total_students
budget_per_student
```


```python
#Top Performing Schools (By Passing Rate) summary table; need school summary first

# Create the GroupBy object based on the "school" column
school_group_df = schools_data_df.groupby(["average_passing"])
school_group_df.head()
```


```python
#add passing rate columns for math & reading
```


```python
#top performing summary table
# Create the GroupBy object based on the "passing" column
top_performing_df = combined_schools_df.groupby(["average_passing"])
top_performing_df.head()
```


```python
#Worst 5 Performing Schools (By Passing Rate) summary table; see worst activity
top_performing_df.tail(5)


```


```python
#average Math Score for students of each grade level (9th, 10th, 11th, 12th) at each school
```


```python
#average Reading Score for students of each grade level (9th, 10th, 11th, 12th) at each school
```


```python
#school performances based on average Spending Ranges (Per Student); create 4 bins
```


```python
#File>Download as>Markdown (.md)
```
