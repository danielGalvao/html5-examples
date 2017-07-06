# HTML5 - examples

### Ambient Light API
[W3c Ambient light Sensor](https://w3c.github.io/ambient-light/) - W3c Specifications

#### Example
  ```javascript
    function updateLightLevel(lightLevel) {
      document.getElementById('lux').innerHTML = Math.round(lightLevel);
      
      if(lightLevel < 50) {
        document.body.className = 'dark';
       } else if(lightLevel < 10000) {
        document.body.className = 'classic';
       } else {
        document.body.className = 'light';
       }
      }
      
      var isOldApiSupported = 'ondevicelight' in window;
      
      if(isOldApiSupported) {
        window.addEventListener('devicelight', function(event) {
           updateLightLevel(event.value);
        });
      } else {
        document.querySelector('.js-api-support').removeAttribute('hidden');
        var sensor = new AmbientLightSensor();
        
	// starting
        sensor.start();
        
        sensor.addEventListener('change', function(event) {
          updateLightLevel(event.reading.illuminance);
        });
      }
  ````

### Device Orientation
[Device Orientation](https://www.w3.org/TR/orientation-event/) - W3c Specifications

#### Example
```javascript
  var imagem = document.querySelector('img')
  window.addEventListener('deviceorientation', function(event) {
    var lr = event.gamma;
    var fb = event.beta;
    imagem.style.transform = 'rotate('+lr+'deg) rotate3d(1,0,0,'+(fb*-1)+'deg)';
  });
 ````
 
 
### Online State
[Online State](https://html.spec.whatwg.org/multipage/offline.html#navigator.online) - W3c Specifications

#### Example
```javascript
  var statusElem = document.getElementById('status');
    var statusElemP = document.getElementsByTagName('p');
    setInterval(function () {
      statusElemP[0].className = navigator.onLine ? 'online' : 'offline';
      statusElem.innerHTML = navigator.onLine ? 'online' : 'offline';
    }, 250);
 ````
 
 ### Page Visibility
[Page Visibility](https://w3c.github.io/page-visibility/) - W3c Specifications

#### Example
```javascript
  document.addEventListener('visibilitychange', function () {
      if (document.hidden) {
        console.log('inativo');
        document.getElementsByTagName('title')[0].innerHTML = 'Saiu da página';
      } else {
        console.log('ativo');
        document.getElementsByTagName('title')[0].innerHTML = 'Olhando a página';
      }
    });
 ````
