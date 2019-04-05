// in the javascript
const focusableElements = document.body.querySelectorAll('a[href], button, input, submit, select');

let mouseActive = false;

focusableElements.forEach((focusableElement)=>{
	focusableElement.addEventListener('mousedown.focusHelper', ()=> {
        mouseActive = true;
        setTimeout(() =>{
	        mouseActive = false;
        }, 100);
	});

	focusableElement.addEventListener('focus', (e) => {
	    if(!mouseActive) { 
		    focusableElement.classList.add('focused');
		}
	});

	focusableElement.addEventListener('blur', (e) => {
		focusableElement.classList.remove('focused');
	});
});


// in the CSS
 .focused {
     border: 3px solid red!important;
 }