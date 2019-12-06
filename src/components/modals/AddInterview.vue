<template>
  <div>
    <div id="open-inter" class="modal-window">
      <div>
        <a href="#Close" title="Close" class="modal-close">X</a>
        <form action>
          <h1>Nýtt viðtal</h1>
          <div class="row">
            <div class="col-75">
              <input type="text" id="lname" name="lastname" placeholder="Your last name.." />
            </div>
          </div>
          <div class="row">
            <div class="col-75">
              <select id="teachers" name="teachers">
                <option value="S mári">Smári</option>
                <option value="Pedro">Pedro</option>
                <option value="Jonathan">Jonathan</option>
              </select>
            </div>
          </div>
          <div class="row">
            <div class="col-75">
              <textarea
                id="subject"
                name="subject"
                placeholder="Nánari lýsing"
                style="height:200px"
              ></textarea>
            </div>
          </div>
          <div class="row">
            <input type="submit" value="Submit" />
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>


<style lang="scss" scope>
input[type="text"],
select,
textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  resize: vertical;
}

input[type="submit"] {
  background-color: #4caf50;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  float: right;
}

input[type="submit"]:hover {
  background-color: #45a049;
}

.col-25 {
  float: left;
  width: 25%;
  margin-top: 6px;
}

.col-75 {
  float: left;
  width: 75%;
  margin-top: 6px;
}

/* Clear floats after the columns */
.row:after {
  content: "";
  display: table;
  clear: both;
}

/* Responsive layout - when the screen is less than 600px wide, make the two columns stack on top of each other instead of next to each other */
@media screen and (max-width: 600px) {
  .col-25,
  .col-75,
  input[type="submit"] {
    width: 100%;
    margin-top: 0;
  }
}

// ********** MEDIA QUERIES **********

// *** MOBILE SIZE ***
@media only screen and (max-width: 900px) {
}
// *** DESKTOP SIZE ***
@media only screen and (min-width: 900px) {
}
</style>
