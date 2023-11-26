```js
const revealPassword = document.querySelector('.reveal-password');
const passwordField = document.querySelector('.password-field');
const passwordAnnounce = document.querySelector('.password-announce');

if (revealPassword && passwordField && passwordAnnounce) {
  revealPassword.hidden = false;
  passwordField.classList.add('has-js');
  
  revealPassword.addEventListener('click', (event) => {
    let isPressed = revealPassword.getAttribute('data-pressed') === 'true';
    if (isPressed) {
    passwordField.type = 'password';
      revealPassword.innerText = revealPassword.dataset.textShow;
      passwordAnnounce.innerText = passwordAnnounce.dataset.textHidden;
    } else {
    passwordField.type = 'text';
    revealPassword.innerText = revealPassword.dataset.textHide;
      passwordAnnounce.innerText = passwordAnnounce.dataset.textShown;
    }
    revealPassword.setAttribute('data-pressed', String(!isPressed));
  });
   
}

```