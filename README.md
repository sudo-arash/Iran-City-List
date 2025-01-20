# Iran Cities and Provinces JavaScript List

A simple JavaScript list of cities and provinces in Iran, designed to work with `<select>` elements. This allows users to select a province and dynamically populate a list of cities for that province.

## How to Use

1. **Include the JavaScript File**:  
   Add the `city.js` file to your HTML document.

   ```html
   <script src="city.js"></script>
   ```

2. **Create the Province Dropdown**:  
   Add a `<select>` element for the provinces. The `onChange` event should call the `irancitylist` function with the selected province value.

   ```html
   <select name="state" onChange="irancitylist(this.value);">
       <option value="0">لطفا استان را انتخاب نمایید</option>
       <option value="تهران">تهران</option>
       <option value="گیلان">گیلان</option>
       <option value="آذربایجان شرقی">آذربایجان شرقی</option>
       <!-- Add more provinces here -->
   </select>
   ```

3. **Create the City Dropdown**:  
   Add a `<select>` element for the cities. This will be dynamically populated based on the selected province.

   ```html
   <select name="city" id="city">
       <option value="0">لطفا شهر را انتخاب نمایید</option>
   </select>
   ```

4. **JavaScript Function**:  
   The `irancitylist` function in `city.js` will handle the dynamic population of cities based on the selected province.

   ```javascript
   function irancitylist(state) {
       const citySelect = document.getElementById("city");
       citySelect.innerHTML = "";

       if (!state || !citiesData[state]) {
           citySelect.appendChild(new Option("لطفا شهر را انتخاب نمایید", "0"));
           return;
       }

       citiesData[state].forEach((city, index) => {
           citySelect.appendChild(new Option(city, index === 0 ? "0" : city));
       });
   }
   ```

## Example HTML

Here’s a complete example of how to use the script:

```html
<!DOCTYPE html>
<html lang="fa">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Iran Cities and Provinces</title>
</head>
<body>
    <label for="state">استان:</label>
    <select name="state" id="state" onChange="irancitylist(this.value);">
        <option value="0">لطفا استان را انتخاب نمایید</option>
        <option value="تهران">تهران</option>
        <option value="گیلان">گیلان</option>
        <option value="آذربایجان شرقی">آذربایجان شرقی</option>
        <!-- Add more provinces here -->
    </select>

    <label for="city">شهر:</label>
    <select name="city" id="city">
        <option value="0">لطفا شهر را انتخاب نمایید</option>
    </select>

    <script src="city.js"></script>
</body>
</html>
```

## Data Structure

The `citiesData` object in `city.js` contains a list of provinces as keys, and each province key maps to an array of cities. The first item in each city array is a placeholder text (`"لطفا شهر را انتخاب نمایید"`).

Example of `citiesData` structure:

```javascript
const citiesData = {
    تهران: [
        "لطفا شهر را انتخاب نمایید",
        "احمد آباد مستوفی",
        "ادران",
        // More cities...
    ],
    گیلان: [
        "لطفا شهر را انتخاب نمایید",
        "احمد سرگوراب",
        "اسالم",
        // More cities...
    ],
    // More provinces...
};
```

## Notes

- Ensure the province values in the `<select>` element match the keys in the `citiesData` object.
- The first option in both the province and city dropdowns is a placeholder with the value `"0"`.
