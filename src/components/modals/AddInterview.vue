<template>
  <div>
    <div id="open-inter" class="modal-window">
      <div>
        <a href="#home" title="Close" class="modal-close">X</a>
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


<style lang="scss" >
// ********** MEDIA QUERIES **********

// *** MOBILE SIZE ***
@media only screen and (max-width: 900px) {
}
// *** DESKTOP SIZE ***
@media only screen and (min-width: 900px) {
}
</style>
