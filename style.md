```css
* {
    margin: 0;
    padding: 0;
}

.container {
    background-image: url('sky1\ \(1\).jpg');
    overflow: hidden;
    height: 100%;
    width: 100%;
}

.side-road {
    position: relative;
    top: 15pc;
    height: 190px;
    background-image: url('city\ \(2\).png');
    background-size: cover;
    animation: side-road .5s linear infinite;
    width: 150%;
}

.road {
    position: relative;
    top: 33pc;
    height: 100px;
    background-image: url('road\ \(1\).jpg');
    animation: road 1s linear infinite;
    background-size: cover;
    width: 500%;
}

.moving-car {
    height: 195px;
    animation: moving-car .1s linear infinite;
}

.front {
    position: relative;
    animation: wheel .5s linear infinite;
    height: 90px;
    left: 13vh;
}

.back {
    position: relative;
    height: 90px;
    left: 45vh;
    animation: wheel .5s linear infinite;
}

@keyframes moving-car {
    0% {
        transform: translateY(0px);
    }

    50% {
        transform: translateY(-2px);
    }

    10% {
        transform: translateY(2px);
    }
}

@keyframes wheel {
    100% {
        transform: rotate(360deg)
    }
}

@keyframes road {
    100% {
        transform: translateX(-3500px)
    }
}
```
@keyframes side-road {
    100% {
        transform: translateX(-1500px)
    }
}
