<template>
  <footer class="footer">
    <div class="contact-links">
      <a
        id="profile-link"
        href="https://github.com/lauramarcq"
        target="_blank"
        class="btn contact-details"
        ><i class="fa-brands fa-github"></i> GitHub</a
      >
      <a href="mailto:laura.valdivia@gmail.com" class="btn contact-details"
        ><i class="fa-solid fa-at"></i> Email me</a
      >
      <a
        href="https://www.linkedin.com/in/laura-valdivia-3b967113"
        class="btn contact-details"
        target="_blank"
        ><i class="fa-brands fa-linkedin"></i> LinkedIn
      </a>
    </div>
    <p>This is my own website and it will always be a work in progress.</p>
    <p>&copy; Laura Marcq Laura Valdivia</p>
  </footer>
</template>

<script>
export default {}
</script>

<style>
.footer {
  background-color: #232133;
  /* min-height: 200px; */
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  margin: 20px;
  gap: 10px;
  max-height: fit-content;
}

.contact-links {
  text-align: center;
  a {
    padding: 10px;
  }
}

p {
  text-align: center;
}
</style>
