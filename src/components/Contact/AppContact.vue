<template>
  <section class="contact-me">
    <div class="container">
      <h2>Contact Me</h2>
      <p>Feel free to reach out to me via phone, Instagram, or Telegram!</p>
      <div class="contact-cards">
        <div class="contact-card">
          <h3>📞 Phone</h3>
          <p>+998 90 123 45 67</p>
        </div>
        <div class="contact-card">
          <h3>📸 Instagram</h3>
          <p>
            <a href="https://instagram.com/mahfuza_0509" target="_blank">@mahfuza_0509</a>
          </p>
        </div>
        <div class="contact-card">
          <h3>💬 Telegram</h3>
          <p>
            <a href="https://t.me/mahfuza_3105" target="_blank">@mahfuza_3105</a>
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "ContactMe",
};
</script>

<style scoped>
.contact-me {
  padding: 60px 20px;
  background: linear-gradient(to right, #e9e0fa, #ffffff);
  font-family: 'Arial', sans-serif;
  text-align: center;
  color: #333;
}

.contact-me h2 {
  font-size: 2.5em;
  margin-bottom: 20px;
}

.contact-me p {
  margin-bottom: 40px;
  font-size: 1.1em;
}

.contact-cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
}

.contact-card {
  background: #fff;
  border-radius: 15px;
  padding: 20px 25px;
  width: 220px;
  box-shadow: 0 6px 15px rgba(0,0,0,0.1);
  transition: transform 0.3s, box-shadow 0.3s;
}

.contact-card h3 {
  margin-bottom: 10px;
  font-size: 1.2em;
}

.contact-card a {
  color: #001aff;
  text-decoration: none;
}

.contact-card a:hover {
  text-decoration: underline;
}

.contact-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0,0,0,0.15);
}
</style>
