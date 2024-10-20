# -bre03-projet-paint-


function selectColor(event)
{
    let colorBox = event.target;
    let color = colorBox.style.backgroundColor;

    sessionStorage.setItem("selectedColor", color);
}

function getSelectedColor()
{
    if(sessionStorage.getItem("selectedColor"))
    {
        return sessionStorage.getItem("selectedColor");
    }

    return null;
}

function loadPalette(palette)
{
    // le code de l'étape 1 se passe ici
    
    const headerDivsDOM = document.querySelectorAll('header>div');
    
       for (let i = 0; i < headerDivsDOM.length; i++) {
        if (i < palette.length) {
            headerDivsDOM[i].style.backgroundColor = palette[i];
        }
    }
} 
        
window.addEventListener("DOMContentLoaded", function(){
    loadPalette(["#22f6f3", "#3daf7e", "#ffffff", "#ec8236", "#a9a7ee", "#ecc606", "#f783f2", "#e89e80"]);

    // le code de l'étape 2 se passe ici
    
    const headerDivsDOM = document.querySelectorAll('header>div');

      for (let i = 0; i < headerDivsDOM.length; i++) {
        headerDivsDOM[i].addEventListener ('click',selectColor);
      }    
        console.log(getSelectedColor());
    
    // le code de l'étape 3 se passe ici

   const mainDivsDOM = document.querySelectorAll('main>div div');
    
    for (let i = 0; i < mainDivsDOM.length; i++){ 
        mainDivsDOM[i].addEventListener ('click', function() {
        let color = getSelectedColor();
        
        
        if (mainDivsDOM[i].style.backgroundColor) {
                
             mainDivsDOM[i].style.backgroundColor = "";
                
            } 
            else if (color)
            {
             mainDivsDOM[i].style.backgroundColor = color;
            }
        });
    }
});
