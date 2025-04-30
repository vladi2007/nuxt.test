<script>

</script>

<template>
    <div class = "background">

                    <h1 class="header1">Вход</h1>
                        <div class = "cnotainer">
                            <div class = "item">
                                <div class = "txt">                                  
                                    <form class = "Mail" id = "entrance-form" action ="#" method ="get" >
                                        <div class="form">
                                            <input type ="email" name="username" id="mail-field" placeholder="Почта" class="base-input" required>
                                            <input type ="password" name="password" id="password-field" placeholder="Пароль" class="base-input" minlength="8" maxlength="20" required>
                                            <p><input class="show-password" type="checkbox" id="show-pass"> 
                                            <label class="checkbox-label" for="show-pass">Показать пароль</label> 
                                            </p>

                                            <div class = "log-in-button"><button type="submit" class="enter-submit-button-usual-button">Вход</button></div>
                                        </div>
                                    </form>
                                    <div class = "sign-in-button">
                                        <p><a class ="sign-in-button-item" href ="/register" id="sign-in-field" >Нет аккаунта?</a></p>
                                    </div>  
                                </div>      
                            </div>       
                        </div>
                </div>
</template>

<style>
@import url("~/assets/css/index.css");
</style>
