<template>
  <div class="testimonial">
    <h1>Testimonials</h1>
    <div class="testimonial-container">
      <div v-for="list in testimonialList" class="testimonial-box">
        <p><strong>{{ list.name }} - {{ list.position }}</strong></p>
        <p>{{ list.comment }}</p>
      </div>
    </div>
    <div class="testimonial-form">
      <div>
        <h2>Leave us a testimonial</h2>
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm" @submit.prevent="submitForm('ruleForm')">
          <el-form-item prop="name" class="two-columns">
            <el-input v-model="ruleForm.name" placeholder="Your Name"></el-input>
          </el-form-item>
          <el-form-item prop="position" class="two-columns">
            <el-input v-model="ruleForm.position" placeholder="Position Title"></el-input>
          </el-form-item>
          <el-form-item prop="comment">
            <el-input type="textarea" v-model="ruleForm.comment" placeholder="Your Comments"></el-input>
          </el-form-item>
          <el-button type="primary" @click="submitForm('ruleForm')">Submit</el-button>
        </el-form>
      </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data: function () {
    // If the words are more than 50 words, show an error message
    var wordCount1 = (rule, value, callback) => {
      if (value.split(' ').length >= 50) {
        callback(new Error('This field cannot be more than 50 words'));
      } else {
        callback();
      }
    };
    // If the words are more than 120 words, show an error message
    var wordCount2 = (rule, value, callback) => {
      if (value.split(' ').length >= 120) {
        callback(new Error('This field cannot be more than 120 words'));
      } else {
        callback();
      }
    };
    return {
      testimonialList: [],
      ruleForm: {
        name: "",
        position: "",
        comment: ""
      },
      rules: {
        name: [
          {
            required: true,
            message: "This field is required"
          },
          {
            validator: wordCount1,
            trigger: "blur"
          }
        ],
        position: [
          {
            required: true,
            message: "This field is required",
          },
          {
            validator: wordCount1,
            trigger: "blur"
          }
        ],
        comment: [
          {
            required: true,
            message: "This field is required"
          },
          {
            validator: wordCount2,
            trigger: "blur"
          }
        ]
      }
    };
  },
  methods: {
    submitForm(formName) {
      // Check if all the required fields are filled, and add the testimonial
      // If not, show errors under the unfilled fields
      this.$refs[formName].validate(valid => {
        if (valid) {
          const obj = {
            'name' : this.ruleForm.name,
            'position' : this.ruleForm.position,
            'comment' : this.ruleForm.comment
          };
          axios
          .post("https://mats0035-midterm-axios.firebaseio.com/data.json", obj)
          .then(response=>{
            // get the new data from the database and add to testimonial
            axios
            .get("https://mats0035-midterm-axios.firebaseio.com/data.json")
            .then(response => {
              console.log(response.data);
              if(response.data)this.testimonialList = response.data;
            })

          });
        } else {
          return false;
        }
      });
    }
  },
  created() {
    axios
    .get("https://mats0035-midterm-axios.firebaseio.com/data.json")
    .then(response => {
       console.log(response.data);
      if(response.data)this.testimonialList = response.data;
    })
    .catch(error => {
      console.log("There was an error in getting data: " + error.response);
    });
  }
}
</script>

<style>
  .testimonial {
    max-width: 800px;
    margin: auto;
    text-align: left;
    padding-top: 100px;
    padding-bottom: 70px;
  }

  .dialog-container {
    display: flex;
    margin: auto 20px;
    text-align: left;
  }

  .testimonial-container {
    display: flex;
    flex-wrap: wrap;
    margin-bottom: 20px;
    margin-left: 6px;
  }

  .testimonial-form {
    border: 1px solid #160a4d;
    padding-bottom: 60px;
    margin: 10px;
  }

  .testimonial-form > div {
    position: relative;
    margin: auto;
    width: 80%;
  }

  .testimonial-box {
    flex: 0 calc(50% - 40px);
    margin: 5px;
    padding: 10px;
    background-color: #e0daff;
  }

  .testimonial-box p {
    margin: 5px;
  }

  .testimonial-box:nth-child(odd), .two-columns:first-child {
    margin-right: 20px;
  }

  .two-columns {
    width: calc(50% - 10px) !important;
    display: inline-block;
  }

  .el-button--primary {
    float: right;
    margin-bottom: 100px !important;
  }
</style>
