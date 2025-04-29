# Lifestyle Recommendation Form for Elementor

A responsive, customizable lifestyle recommendation form designed specifically for WordPress sites using Elementor page builder. This form allows users to input their personal details and receive personalized recommendations based on their age, family status, and career stage.


## Features

- 🎨 Clean, modern design with customizable colors
- 📱 Fully responsive across all devices
- ✅ Client-side form validation
- 🔄 Loading animation during submission
- 🧠 Smart recommendation logic
- 🌐 Dynamic redirects based on user inputs
- 🧮 Special logic for age 60+ handling

## Installation

### Option 1: Using the HTML Widget in Elementor

1. Edit your page with Elementor
2. Drag and drop the HTML widget to your desired section
3. Copy the entire code from `lifestyle-recommendation-form.html`
4. Paste it into the HTML widget
5. Save and update your page

### Option 2: Using a Custom HTML Block in WordPress

1. Edit your page using the WordPress block editor
2. Add a Custom HTML block
3. Copy the entire code from `lifestyle-recommendation-form.html`
4. Paste it into the Custom HTML block
5. Update your page

## Customization

### Changing Colors

The form uses CSS variables for easy color customization. Look for these lines at the beginning of the `<style>` section:

```css
.lifestyle-form-wrapper {
    background-color: #FFF1F1;
    color: #333333;
    /* other styles */
}

.lifestyle-submit-button {
    background-color: #990000;
    /* other styles */
}

.lifestyle-submit-button:hover {
    background-color: #800000;
}
```

Modify these color codes to match your website's color scheme.

### Adjusting Form Fields

The form includes the following fields:
- Full Name
- Email Address
- Age Range
- Family Status
- Career Stage

If you need to add or remove fields, locate the form structure in the HTML:

```html
<form id="lifestyleRecommendationForm">
    <!-- Form fields here -->
</form>
```

Edit this section to add, remove, or modify fields. Make sure to update the validation logic in the JavaScript if you make changes.

## Recommendation Logic

The recommendation system works by matching a combination of Age, Family Status, and Career Stage to a predefined URL. The mapping is defined in the `lifestyleRecommendationData` array:

```javascript
const lifestyleRecommendationData = [
    { age: "18-30", familyStatus: "Single", careerStage: "Unemployed", redirectUrl: "https://[YOUR-DOMAIN]/recommendation/path-1/" },
    // more mappings...
];
```

### Updating Recommendations

To update the recommendation URLs:

1. Locate the `lifestyleRecommendationData` array in the JavaScript section
2. Modify the `redirectUrl` values to your desired destination pages
3. Add or remove entries as needed for different combinations

## Special Age Logic

The form includes special handling for users who select "60 and above" for their age. When this age range is selected, the Career Stage field automatically updates to only show "Retired" as an option.

If you need to modify this behavior:

1. Find the age change event listener in the JavaScript section:
   ```javascript
   ageSelect.addEventListener('change', function() {
       if (this.value === '60 and above') {
           // Special handling for 60+ age group
       } else {
           // Normal options
       }
   });
   ```
2. Modify the logic as needed

## Validation

The form validates all fields before submission:
- All fields are required
- Email format is validated
- Error messages appear under each field when validation fails

The validation function can be customized in the JavaScript section:

```javascript
function validateLifestyleForm() {
    // Validation logic
}
```

## Loading Animation

When the form is submitted and validation passes, a loading animation appears while the system determines the appropriate recommendation. This delay is set to 1.8 seconds but can be adjusted:

```javascript
setTimeout(function() {
    findAndRedirectLifestyle(age, familyStatus, careerStage);
}, 1800); // 1.8 seconds delay for the loader animation
```

## Browser Compatibility

This form is compatible with:
- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers (iOS Safari, Android Chrome)

## Troubleshooting

### Form Styling Issues in Elementor

If you experience styling conflicts with Elementor:

1. Make sure all CSS is properly namespaced (all classes should start with `lifestyle-`)
2. Check that no global styles are being applied (styles should only target elements within the form container)
3. Try adjusting the container width in Elementor settings

### Form Not Submitting

If the form doesn't redirect after submission:

1. Check browser console for JavaScript errors
2. Verify that the entered combination exists in the `lifestyleRecommendationData` array
3. Ensure the URLs in the array are correctly formatted and accessible

## License

MIT License - Feel free to use, modify, and distribute this code for personal or commercial projects.

## Support

For issues, questions, or customization requests, please open an issue on this repository 

## Credits

Developed by Emmanuel Eluwa
