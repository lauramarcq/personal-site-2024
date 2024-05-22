<template>
  <div class="welcome-wrapper">
    <div class="message-container">
      <div class="message"><span>Hey</span>, I'm Laura</div>
      <div class="message-details">
        I am a web developer from Chile living in Bath, UK for the last 13 years.
      </div>
    </div>
    <div class="image-container">
      <img
        class="profile-image"
        src="@/assets/profile_image-removebg-preview.png"
        alt="profile-image"
      />
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.welcome-wrapper {
  background-color: #252537;
  min-width: 100vw;
}
.image-container {
  background-color: #ee595d;
  border-radius: 50%;
}
img {
  height: 100%;
  width: 100%;
  border-radius: 50%;
}
.message-details {
  margin-top: 10px;
  font-size: 1.2rem;
  font-weight: 200;
  font-family: Verdana, Tahoma, sans-serif;
  margin-left: 20px;
  margin-right: 20px;
  color: rgba(255, 255, 255, 0.899);
}
.message {
  margin-top: 20px;
  font-size: 1.5rem;
  font-weight: 900;
  font-family: Verdana, Tahoma, sans-serif;
  color: white;
  span {
    color: #ee595d;
    font-weight: 900;
  }
}
@media only screen and (max-width: 767px) {
  .welcome-wrapper {
    min-height: calc(100vh - 200px);
    font-weight: 300;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
  .welcome-wrapper .image-container {
    height: 250px;
    width: 250px;
    align-self: center;
  }
  .message-container {
    display: flex;
    align-items: flex-start;
    flex-direction: column;
    justify-content: center;
    margin-bottom: 5%;
  }

  .message {
    margin-top: 20px;
    font-size: 1.5rem;
    font-weight: 900;
    align-self: center;
  }

  .message-details {
    font-size: 1rem;
    margin-left: 20px;
    margin-right: 20px;
    text-align: center;
  }
}
@media only screen and (min-width: 768px) and (max-width: 1023px) {
  /* Styles for tablet devices */
  .welcome-wrapper {
    min-height: calc(100vh - 350px);
    display: flex;
    flex-direction: column;
    justify-content: space-around;
  }

  .welcome-wrapper .image-container {
    height: 350px;
    width: 350px;
    align-self: flex-end;
    align-self: center;
  }
  .message-container {
    display: flex;
    flex-direction: column;
    margin-bottom: 5%;
  }

  .message {
    margin-top: 20px;
    font-size: 1.5rem;
    font-weight: 900;
    align-self: center;
  }

  .message-details {
    margin-top: 10px;
    font-size: 1rem;
    font-weight: 200;
    margin-left: 20px;
    margin-right: 20px;
    text-align: center;
  }
}
@media only screen and (min-width: 1024px) {
  /* Styles for desktop devices */
  .welcome-wrapper {
    min-height: calc(100vh - 400px);
    min-width: 100vw;
    min-height: 70vh;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
  }
  .welcome-wrapper .image-container {
    height: 450px;
    width: 450px;
    align-self: flex-end;
    margin-top: 2%;
  }

  .message-container {
    display: flex;
    align-items: flex-start;
    flex-direction: column;
    max-width: 50%;
  }

  .message {
    margin-top: 50px;
    margin-left: 20px;
    margin-right: 20px;
    font-size: 2rem;
    font-weight: 900;
  }

  .message-details {
    margin-top: 10px;
    font-size: 1.2rem;
    font-weight: 200;
    margin-left: 20px;
    margin-right: 20px;
  }
}
</style>
