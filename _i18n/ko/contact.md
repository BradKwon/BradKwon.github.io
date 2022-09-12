<p>가능한 빨리 답장 드릴게요!</p>
<!-- Contact Form - Enter your email address on line 19 of the mail/contact_me.php file to make this form work. -->
<!-- WARNING: Some web hosts do not allow emails to be sent through forms to common mail hosts like Gmail or Yahoo. It's recommended that you use a private domain email address! -->
<!-- NOTE: To use the contact form, your site must be on a live web host with PHP! The form will not work locally! -->
<form name="sentMessage" id="contactForm" action="https://formspree.io/f/moqydayl" method="POST" novalidate>
    <div class="row control-group">
        <div class="form-group col-xs-12 floating-label-form-group controls">
            <label>이름</label>
            <input type="text" class="form-control" placeholder="이름" id="name" name="name" required data-validation-required-message="이름을 입력해 주세요.">
            <p class="help-block text-danger"></p>
        </div>
    </div>
    <div class="row control-group">
        <div class="form-group col-xs-12 floating-label-form-group controls">
            <label>이메일</label>
            <input type="email" class="form-control" placeholder="이메일 주소" id="email" name="email" required data-validation-required-message="이메일 주소를 입력해 주세요.">
            <p class="help-block text-danger"></p>
        </div>
    </div>
    <div class="row control-group">
        <div class="form-group col-xs-12 floating-label-form-group controls">
            <label>연락처</label>
            <input type="tel" class="form-control" placeholder="연락처" id="phone" name="phone">
            <p class="help-block text-danger"></p>
        </div>
    </div>
    <div class="row control-group">
        <div class="form-group col-xs-12 floating-label-form-group controls">
            <label>메시지</label>
            <textarea rows="5" class="form-control" placeholder="메시지" id="message" name="message" required data-validation-required-message="메시지를 입력해 주세요."></textarea>
            <p class="help-block text-danger"></p>
        </div>
    </div>
    <br>
    <div id="success"></div>
    <div class="row">
        <div class="form-group col-xs-12">
            <button type="submit" class="btn btn-default">보내기</button>
        </div>
    </div>
</form>