<template>
  <div class="wrapper">
    <main>
      <form
        action="https://script.google.com/macros/s/AKfycbzluZPm-z7jQNXhXo0M4ffgnjMic1wtcfjwL25-El2E0k512LQ/exec"
        class="form-box">
        <input
          name="SPREADSHEET_ID"
          type="hidden"
          value="1flDmW0Hsk8p0CqpFsLoeXRn76tRxYupjjgQgRPvUaS8"
        >
        <input name="SHEET_NAME" type="hidden" value="フォームデータ">
        <h1>お問い合わせ</h1>
        <div class="form-item-box">
          <label class="control-label">Mail</label>
          <div>
            <input type="email" class="form-control" name="your-email" placeholder="ypur@email.com">
          </div>
        </div>
        <div class="form-item-box">
          <label class="control-label">お名前</label>
          <div>
            <input type="text" class="form-control" name="your-name" placeholder="Your Name">
          </div>
        </div>
        <div class="form-item-box">
          <label class="control-label">メッセージ <span class="label-required">必須</span></label>
          <div>
            <textarea
              class="form-control"
              name="your-message"
              placeholder="Message"
              rows="8"
              required
              id="message">
            </textarea>
          </div>
        </div>
        <div class="form-item-box">
          <div class="form-button-box">
            <button class="form-button" type="submit" v-on:click="sendMessage()">Submit</button>
          </div>
        </div>
      </form>
    </main>
  </div>
</template>

<script>
import $ from 'jquery';

window.jQuery = $;
window.$ = $;

export default {
  title: 'Contact',
  description: 'お問い合わせページ',
  methods: {
    sendMessage() {
      const form = $('form');
      const submitBtn = form.find('button[type=submit]');
      if ($('#message').val()) {
        return false;
      }
      $.ajax({
        url: form.attr('action'),
        dataType: 'jsonp',
        data: form.serialize(),
        beforeSend() {
          return submitBtn.prop('disabled', true);
        },
        complete() {
          return submitBtn.prop('disabled', false);
        },
        jsonpCallback: 'console.log',
        error() {},
      });
      return false;
    },
  },
};
</script>
