<template>
  <survey :survey="survey" />
</template>

<script>
import * as Survey from "survey-vue";

import "survey-vue/modern.css";
import "./index.css";

Survey.StylesManager.applyTheme("modern");

export default {
  name: "surveyjs-component",
  data() {
    var json = {
      title: "Product Feedback Survey Example (中国地方志数据库)",
      showProgressBar: "top",
      locale: "zh-cn",
      pages: [
        {
          questions: [
            {
              name: "date",
              type: "datepicker",
              inputType: "date",
              title: "Your favorite date:",
              dateFormat: "mm/dd/yy",
              isRequired: true,
            },
            {
              type: "matrix",
              name: "1_Quality",
              title: {
                default:
                  "Please indicate if you agree or disagree with the following statements",
                "zh-cn": "请指出您是否同意以下陈述",
              },
              columns: [
                {
                  value: 1,
                  text: {
                    default: "Strongly Disagree",
                    "zh-cn": "强烈反对",
                  },
                },
                {
                  value: 2,
                  text: "Disagree",
                },
                {
                  value: 3,
                  text: "Neutral",
                },
                {
                  value: 4,
                  text: "Agree",
                },
                {
                  value: 5,
                  text: "Strongly Agree",
                },
              ],
              rows: [
                {
                  value: "1.1 affordable",
                  text: "Product is affordable",
                },
                {
                  value: "1.2 does what it claims",
                  text: "Product does what it claims",
                },
                {
                  value: "1.3 better then others",
                  text: "Product is better than other products on the market",
                },
                {
                  value: "1.4 easy to use",
                  text: "Product is easy to use",
                },
              ],
            },
            {
              type: "rating",
              name: "2_satisfaction",
              title: "How satisfied are you with the Product?",
              mininumRateDescription: "Not Satisfied",
              maximumRateDescription: "Completely satisfied",
            },
            {
              type: "rating",
              name: "2.5_recommend friends",
              visibleIf: "{satisfaction} > 3",
              title:
                "How likely are you to recommend the Product to a friend or co-worker?",
              mininumRateDescription: "Will not recommend",
              maximumRateDescription: "I will recommend",
            },
            {
              type: "comment",
              name: "3_suggestions",
              title: "What would make you more satisfied with the Product?",
            },
          ],
        },
        {
          questions: [
            {
              type: "radiogroup",
              name: "4_price to competitors",
              title: "Compared to our competitors, do you feel the Product is",
              choices: [
                "Less expensive(更便宜)",
                "Priced about the same",
                "More expensive(更貴)",
                "Not sure",
              ],
            },
            {
              type: "radiogroup",
              name: "5_price",
              title: "Do you feel our current price is merited by our product?",
              choices: [
                "correct|Yes, the price is about right是的，價格差不多",
                "low|No, the price is too low for your product",
                "high|No, the price is too high for your product他的价格对你的产品来说太高了",
              ],
            },
            {
              type: "checkbox",
              name: "6_fruit",
              title: {
                default: "What fruit do you like",
              },
              description: "This is your personal choice",
              choices: [
                {
                  value: "apple",
                  text: "Apple",
                },
                {
                  value: "orangle",
                  text: "Orangle",
                },
                {
                  value: "rice",
                  text: "Rice",
                },
              ],
            },

            {
              type: "multipletext",
              name: "7_pricelimit",
              title: "What is the... ",
              items: [
                {
                  name: "mostamount",
                  title:
                    "Most amount you would every pay for a product like ours",
                },
                {
                  name: "leastamount",
                  title: "The least amount you would feel comfortable paying",
                },
              ],
            },
          ],
        },
        {
          questions: [
            {
              type: "text",
              name: "8_email",
              title:
                'Thank you for taking our survey. Please enter your email address, then press the "Submit" button.',
            },
          ],
        },
      ],
    };

    const survey = new Survey.Model(json);

    return {
      survey: survey,
    };
  },
};
</script>

<style scoped>
</style>
