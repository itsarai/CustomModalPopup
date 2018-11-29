# CustomModalPopup
<h1>Learn how to create a Custom Modal Popup with CSS and JavaScript. A modal is a dialog box/popup window that is displayed on top of the current page.</h1>

<h2>Features</h2>
<ol>
  <li>When the user clicks the button, open the modal</li>
  <li>When the user clicks on (x), close the modal</li>
  <li>When the user clicks anywhere outside of the modal, close it</li>
  <li>When the user Press Esc Buttom in Keyboard, close it</li>
  <li>When the user Use Press Back Buttom in Browser/Mobile, close it</li>
</ol>

<h2>Browser support</h2>
<ul>
  <li>Chrome</li>
  <li>Safari</li>
  <li>Firefox</li>
  <li>Edge <em>(latest 2)</em></li>
  <li>Opera</li>
</ul>

<h2>Custom Animated Modal Popup with Header and Footer</h2>
<p>Use only CSS and Javascript</p>

<h2>Model Popup Basic CSS with Animation</h2> 
<pre>
body {font-family:Arial, Helvetica, sans-serif;}
/* The Modal (background) */
.__ar_modal{
    display: none; /* Hidden by default */
    position: fixed; /* Stay in place */
    z-index: 1; /* Sit on top */
    padding-top: 100px; /* Location of the box */
    left: 0;
    top: 0;
    width: 100%; /* Full width */
    height: 100%; /* Full height */
    overflow: auto; /* Enable scroll if needed */
    background-color: rgb(0,0,0); /* Fallback color */
    background-color: rgba(0,0,0,0.4); /* Black w/ opacity */
}
/* Modal Content */
.__ar_modal-content {
    position: relative;
    background-color: #fefefe;
    margin: auto;
    padding: 0;
    border: 1px solid #888;
    width: 80%;
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2),0 6px 20px 0 rgba(0,0,0,0.19);
    -webkit-animation-name: animatetop;
    -webkit-animation-duration: 0.4s;
    animation-name: animatetop;
    animation-duration: 0.4s
}
/* Add Animation */
@-webkit-keyframes animatetop {
    from {top:-300px; opacity:0} 
    to {top:0; opacity:1}
}
@keyframes animatetop {
    from {top:-300px; opacity:0}
    to {top:0; opacity:1}
}
/* The Close Button */
.__ar_modal-close {color:#fff;float:right;font-size:28px;font-weight:bold;}
.__ar_modal-close:hover,
.__ar_modal-close:focus {color:#000;text-decoration:none;cursor:pointer;}
/* The Header/Footer */
.__ar_modal-header{padding:2px 16px;background-color:#5cb85c;color:white;}
.__ar_modal-body  {padding:2px 16px;}
.__ar_modal-footer{padding:2px 16px;background-color:#5cb85c;color:white;}
/* Remove Body Scroll when Model Open */
.__ar_modal-open{overflow:hidden;}
</pre>

<h2>Model Popup Custom Javascript</h2>   
<pre>
// Get the modal
var modal = document.getElementById('__arModal');
// Get the button that opens the modal
var btn = document.getElementById("__arModalBtn");
// Get the <span> element that closes the modal
var span = document.getElementsByClassName("__ar_modal-close")[0];
//Body scrollfix
var bdclass = '__ar_modal-open';
// When the user clicks the button, open the modal 
btn.onclick = function() {
    history.pushState(null, null, window.location.pathname);
    document.body.classList.add(bdclass);
    modal.style.display = "block";
}
// When the user clicks on <span> (x), close the modal
span.onclick = function() {
    document.body.classList.remove(bdclass);
    modal.style.display = "none";
}
// When the user clicks anywhere outside of the modal, close it
window.onclick = function(event) {
    if (event.target == modal) {
        document.body.classList.remove(bdclass);
        modal.style.display = "none";
    }
}
// When the user Press Esc Buttom in Keyboard, close it
window.onkeydown = function (event) {
    event = event || window.event;
    if (event.keyCode == 27) {
        document.body.classList.remove(bdclass);
        modal.style.display = "none";
    }
}
// When the user Use Press Back Buttom in Browser/Mobile, close it
window.onpopstate = function(event) {
    if(modal.style.display == 'none'){
        history.back();
    } else { 
      history.pushState(null, null, window.location.pathname);
      document.body.classList.remove(bdclass);
      modal.style.display = "none";
    }  
}
</pre>
