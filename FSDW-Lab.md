`Note : The programs are not exact out of record`
# Week - 1
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="css/bootstrap.min.css">
</head>
<body>
    <div class="jumbotron text-center bg-dark text-white">
        <h1>CMRIT</h1>
        <small>- All departments in CMRIT</small>
        <div class="container-fluid">
            <div class="row">
            <div class="col-md-3 bg-danger">
                <h1>CSD</h1>
                <p>Data Science</p>
                <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Voluptatem est mollitia explicabo maxime aliquam perferendis beatae corrupti dolorum molestiae eligendi molestias quibusdam unde dolore vitae impedit quis, a officia! Soluta quas tempora repudiandae unde voluptas repellat voluptatibus consequatur obcaecati ad labore. Inventore ratione ex asperiores!</p>
            </div>
            <div class="col-md-3 bg-primary">
                <h1>CSE</h1>
                <p>Data Science</p>
                <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Expedita, ut doloremque unde dolor itaque sint corrupti dicta quod inventore ullam labore molestias saepe ea fuga autem aut recusandae sit facere a, ipsam laborum pariatur consequatur vitae dolore. Expedita iste magnam eius, illum id possimus tempore.</p>
            </div>
            <div class="col-md-3 bg-success">
                <h1>CSM</h1>
                <p>Data Science</p>
                <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Expedita, ut doloremque unde dolor itaque sint corrupti dicta quod inventore ullam labore molestias saepe ea fuga autem aut recusandae sit facere a, ipsam laborum pariatur consequatur vitae dolore. Expedita iste magnam eius, illum id possimus tempore.</p>
            </div>
            <div class="col-md-3 bg-secondary ">
                <h1>AIDS</h1>
                <p>Data Science</p>
                <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Expedita, ut doloremque unde dolor itaque sint corrupti dicta quod inventore ullam labore molestias saepe ea fuga autem aut recusandae sit facere a, ipsam laborum pariatur consequatur vitae dolore. Expedita iste magnam eius, illum id possimus tempore.</p>
            </div>
        </div>
    </div>
</div>
</body>
</html>
```

# Week - 2

`Note : I haven't added fontawesome icons ! `
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <!-- <link rel="stylesheet" href="css/bootstrap.min.css"> -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
    <!-- Bootstrap bundle.min.js is must ! -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz" crossorigin="anonymous"></script>

    <style>
        .container nav ul li a{
            color: white;
        }
    </style>
</head>
<body>
    <div class="container">
        <nav class="navbar bg-dark ">
            <ul class="nav">
                <li class="nav-item">
                    <a href="" class="nav-link">Home</a>
                </li>
                <li class="nav-item">
                    <a href="" class="nav-link">About</a>
                </li>
                <li class="nav-item dropdown">
                    <a href="" class="nav-link dropdown-toggle" data-bs-toggle="dropdown" aria-expanded="false">Dropdown</a>
                    <ul class="dropdown-menu">
                        <li >
                            <a href="" class="dropdown-item text-dark">Item 1</a>
                        </li>
                        <li >
                            <a href="" class="dropdown-item text-dark">Item 2</a>
                        </li>
                        <li >
                            <a href="" class="dropdown-item text-dark">Item 3</a>
                        </li>
                    </ul>
                </li>
            </ul>
        </nav>
    </div>
</body>
</html>
```

# Week - 5

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="css/bootstrap.min.css">
</head>

<body>
    <div class="container" onsubmit="validate()">
        <form action="" name="box" class="form-control">
            <fieldset>

                <h1 class="text-center">Registration Form</h1>
                <label for="">First name</label>
                <input name="user" type="text" class="form-control" required>
                <br>
                <label for="">Last name</label>
                <input name="userLast" type="text" class="form-control" required>
                <br>
                <label for="">Password</label>
                <input type="password" name="pass" class="form-control" required>
                <br>
                <label for="">Email</label>
                <input type="email" name="email" class="form-control" required>
                <br>
                <label for="">Date : </label>
                <input type="date" required>
                <br>
                <br>
                <label for="">Gender :</label>
                <label for="Male">Male
                    <input type="radio" name="gender" id="b1" required>
                </label>

                <label for="Female">
                    Female
                    <input type="radio" name="gender" id="b2" required>
                </label>
                <br>
                <br>
                <!-- Direct to next page -->
                <a href="successSubmit">
                    <input type="submit">
                </a>

            </fieldset>
        </form>
        <script>
            function validate() {
                let name = box.user.value;
                //  Traverse through each letter ..
                for (i in name) {
                    ch = name.charCodeAt(i);
                    if (ch < 65 || ch > 90 && ch < 97 || ch > 122) {
                        alert("Invalid Name");
                    }
                }

                // create same for last name ...
                let lastName = box.userLast.value;
                for (i in lastName) {
                    ch = lastName.charCodeAt(i);
                    if (ch < 65 || ch > 90 && ch < 97 || ch > 122) {
                        alert("Invalid Name");
                    }
                }
                // Password length validator
                let pass1 = box.pass.value;
                if (pass1.length < 5) {
                    alert("Should have more than 5 length");
                }

                // Email validator
                let ema = box.email.value;

                // expression :
                let reg = /^[a-zA-Z][a-zA-Z0-9\.-]+@[a-zA-Z].[a-z]{2,4}.[a-z]{2,4}?$/;
                if (reg.test(ema)) {
                    alert("Good to go!");
                }
                else {
                    alert("Invalid mail")
                }
            }
        </script>
    </div>
</body>
</html>
```

# Week - 6

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Week - 6</title>

    // Bootstrap CSS *must*
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">

    // JQuery CDN *must*
    <script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>

    //Bootstrap JS *must*
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
</head>
<body>
    <div class="container">
        <div id = "myCarousel" class="carousel slide">
            <ol class="carousel-indicators">
                <li class="item1 active"></li>
                <li class="item2"></li>
                <li class="item3"></li>
            </ol>
            <div class="carousel-inner" role = "listbox">
                <div class="item active">
                    <img src="images.jpeg" alt="" height="90%">
                </div>
                <div class="item">
                    <img src="unnamed.jpg" alt="" height="50%">
                </div>
                <div class="item">
                    <img src="images.jpeg" alt="" height="90%">
                </div>
            </div>
            <a class="left carousel-control" href="#myCarousel" role="button">
                <span class="glyphicon glyphicon-chevron-left" aria-hidden="true"></span>
                <span class="sr-only">Prev</span>
            </a>
            <a class="right carousel-control" href="#myCarousel" role="button">
                <span class="glyphicon glyphicon-chevron-right" aria-hidden="true"></span>
                <span class="sr-only">Next</span>
            </a>
        </div>
    </div>

    <script>
        //JQuery
        $(document).ready(function () {
            $("#myCarousel").carousel();
            $(".item1").click(function () {
                $("#myCarousel").carousel(0);
            })
            $(".item2").click(function () {
                $("#myCarousel").carousel(1);
            })
            $(".item3").click(function () {
                $("#myCarousel").carousel(2);
            })
            $(".left").click(function () {
                $("#myCarousel").carousel("prev");
            })
            $(".right").click(function () {
                $("#myCarousel").carousel("next");
            })
        });
    </script>
</body>
</html>
```
