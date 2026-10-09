---
title: "*This One Will Be Different* Bookplates"
permalink: /bookplate/
author_profile: true
published: true

header:
  image: bookplate_social_preview.jpg
---

<style>
.page__hero {
  display: none;
}
</style>
## Request a Signed Bookplate

If you've purchased a copy of *This One Will Be Different*, I'd be happy to send you a
signed **4 things adults shouldn't believe in** bookplate *(free of charge, while supplies last)*.

<div style="display:flex; justify-content:center; align-items:center; gap:15px; margin:1.75em 0;">
  <img src="/images/bookplate.jpg"
       alt="Custom bookplate featuring Santa Claus, the Tooth Fairy, the Easter Bunny, and a publicly funded stadium"
       style="width:48%; height:auto; border-radius:4px;">

  <img src="/images/bookplate_signed.jpg"
       alt="Signed bookplate placed inside This One Will Be Different"
       style="width:48%; height:auto; border-radius:4px;">
</div>


Please provide your mailing information below. If you'd like your bookplate personalized, you may request a brief inscription. Space is limited, and I may not be able to accommodate all requests.

No need to request a bookplate if you're attending the [A Cappella Books event at Manuel's Tavern on October 27](https://www.acappellabooks.com/pages/events/1517/j-c-bradbury-in-conversation-with-rafi-kohan). I'll bring some to the event.

<p class="required-note"><span class="required">*</span> Required</p>

<form id="bookplateForm" novalidate>

<table border="0" width="100%">
<tbody>

<tr>
  <td width="30%">Name (mail recipient)<span class="required">*</span></td>
  <td width="70%">
    <input maxlength="60" name="Name" size="35"
           type="text" autocomplete="name" required>
  </td>
</tr>

<tr>
  <td>Street Address<span class="required">*</span></td>
  <td>
    <input maxlength="80" name="Address" size="35"
           type="text" autocomplete="address-line1" required>
  </td>
</tr>

<tr>
  <td>Address Line 2</td>
  <td>
    <input maxlength="80" name="Address2" size="35"
           type="text" autocomplete="address-line2">
  </td>
</tr>

<tr>
  <td>City<span class="required">*</span></td>
  <td>
    <input maxlength="50" name="City" size="30"
           type="text" autocomplete="address-level2" required>
  </td>
</tr>

<tr>
  <td>State, Province, or Region<span class="required">*</span></td>
  <td>
    <input maxlength="50" name="State" size="25"
           type="text" autocomplete="address-level1" required>
  </td>
</tr>

<tr>
  <td>Postal or ZIP Code<span class="required">*</span></td>
  <td>
    <input maxlength="15" name="PostalCode" size="15"
           type="text" autocomplete="postal-code" required>
  </td>
</tr>

<tr>
  <td>Country<span class="required">*</span></td>
  <td>
    <input maxlength="50" name="Country" size="25"
           type="text" autocomplete="country-name" required>
  </td>
</tr>

<tr>
  <td>Personalization</td>
  <td>
    <input maxlength="60" name="Personalization" size="35"
           type="text" placeholder='For example, "To Fred"'>
    <div class="field-note">
      Leave blank if you would like a signature only. I may not be able to accommodate all requests.
    </div>
  </td>
</tr>

<tr>
  <td>Email<span class="required">*</span></td>
  <td>
    <input maxlength="256" name="Email" size="35"
           type="email" autocomplete="email" required>
    <div class="field-note">
      Please provide your email in case there is a problem with your request.
    </div>
  </td>
</tr>

</tbody>
</table>

<input type="hidden" name="_subject"
       value="New Signed Bookplate Request">

<!-- Spam trap -->
<input type="text" name="_gotcha" style="display:none">

<p style="margin-top:18px;">
  <button id="bookplateSubmit"
          type="button"
          class="btn btn--primary">
    Request a Bookplate
  </button>

  <span id="bookplateStatus"
        style="margin-left:10px;font-weight:600;"
        aria-live="polite"></span>
</p>

</form>

<p style="font-size:0.9em;">
Your information will be used only to send your bookplate and
will not be added to a mailing list or used for any other purpose.
</p>

<p><em>Bookplates are available while supplies last.</em></p>

<style>

.required {
  color: #c00000;
  font-weight: bold;
  margin-left: 2px;
}

.required-note {
  font-size: 0.9em;
  margin-bottom: 10px;
}

.field-note {
  font-size: 0.9em;
  color: #555;
  margin-top: 4px;
}

</style>

<script>
(function () {

  const FORMSPREE = "https://formspree.io/f/mdekvjav";

  const form = document.getElementById("bookplateForm");
  const btn = document.getElementById("bookplateSubmit");
  const status = document.getElementById("bookplateStatus");

  function okRequired() {

    const required = form.querySelectorAll("[required]");

    for (const el of required) {

      if (!el.value || !el.value.trim()) {
        el.focus();
        return false;
      }

    }

    const email = form.querySelector('input[name="Email"]');

    if (email.value &&
        !/^\S+@\S+\.\S+$/.test(email.value.trim())) {

      email.focus();
      return false;

    }

    return true;
  }

  btn.addEventListener("click", async function () {

    if (!okRequired()) {

      status.textContent =
        "Please complete the required fields.";

      return;
    }

    status.textContent = "Submitting…";
    btn.disabled = true;

    try {

      const data = new FormData(form);

      const resp = await fetch(FORMSPREE, {
        method: "POST",
        body: data,
        headers: {
          "Accept": "application/json"
        }
      });

      if (!resp.ok)
        throw new Error("Formspree failed");

      form.reset();

      status.textContent =
        "Thank you! Your bookplate request has been received.";

    }

    catch (e) {

      status.textContent =
        "Submission failed. Please try again.";

      btn.disabled = false;

    }

  });

})();
</script>

<!--
## Get a Signed Bookplate

<img src="/images/bookplate.jpg"
     alt="Signed bookplate for This One Will Be Different"
     style="display:block; max-width:300px; width:100%; height:auto; margin:1.5em auto;">

Have a copy of *This One Will Be Different*? I'll be happy to send you a signed bookplate **free of charge**.

Just fill out the form below with your mailing address and, if you'd like, the name you'd like the bookplate made out to. I'll sign it and send it to you by mail.

**U.S. and international requests are welcome.**

[Request a Signed Bookplate](https://forms.cloud.microsoft/r/xmBy3q5Uc1){: .btn .btn--primary }

Your mailing information will be used **only to send your bookplate** and will not be added to a mailing list or used for any other purpose.

*Bookplates are available while supplies last.*

-->