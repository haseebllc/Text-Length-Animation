live : https://newgithubuser709.github.io/Text-animation/ 

```hash
window.onload = function() {
    animateText();
};

function animateText() {
    var element = document.getElementById("animated__text");

    var texts = ["First Text", "Second Text", "third Text"];
    var currentIndex = 0;

    function animate(currentText) {
        element.textContent = "";

        for (var i = 0; i < currentText.length; i++) {
            setTimeout(
                (function(index) {
                    return function() {
                        element.textContent += currentText[index];
                    };
                })(i),
                i * 300
            );
        }

        setTimeout(function() {
            var interval = setInterval(function() {
                if (element.textContent.length > 0) {
                    var newText = element.textContent.slice(0, -1);
                    element.textContent = newText;
                } else {
                    clearInterval(interval);
                    currentIndex = (currentIndex + 1) % texts.length;
                    animate(texts[currentIndex]);
                }
            }, 300);
        }, currentText.length * 300 + 2000);
    }

    animate(texts[currentIndex]);
}
```
