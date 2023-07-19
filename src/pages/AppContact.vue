<script>
export default {};
</script>

<template>
  <h1>Contact us</h1>

  <form novalidate>
    <div class="mb-3">
      <label for="name" class="form-label">Name</label>
      <input type="text" class="form-control" id="name" />
    </div>

    <div class="mb-3">
      <label for="email" class="form-label">Email address</label>
      <input type="email" class="form-control" id="email" />
    </div>

    <div class="mb-3">
      <label for="message" class="form-label">Message</label>
      <textarea class="form-control" id="message" rows="5"></textarea>
    </div>

    <div class="mb-3 form-check">
      <input type="checkbox" class="form-check-input" id="newsletter" />
      <label class="form-check-label" for="newsletter"
        >Subscribe to newsletter</label
      >
    </div>

    <button type="submit" class="btn btn-primary">Submit</button>
  </form>
</template>

<style></style>
