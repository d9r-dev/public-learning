- Landmarks: Header, Footer, Main, Aside, Nav, Section
- --> haben Rollen, die Screen-Reader helfen
- Wenn mehr als eine von den Landmarks dann mit aria-label beschreiben zum Beispiel <nav
  aria-label="social">
- Aside sollte etwas mit dem Main Content zu tun haben
- Section ist unabhängig vom Main Content
-
- The **<button> element** should be used for any interaction that performs **an action on the current page**. The **<a> element** should be used for any interaction that **navigates to another view**.
- Aus [https://www.w3schools.com/accessibility/accessibility_buttons_links.php](https://www.w3schools.com/accessibility/accessibility_buttons_links.php)
-
- Wenn man aus technischen Gründen das richtige semantische Element nehmen kann, sollte man
  dem Element eine role geben. Baut man einen Button beispielsweise als <a> dann sollte er role="button" bekommen. <button> hat die role bereits eingebaut. Dort wäre es ein Duplikat.
-
- Elemente sollten einen Namen haben. `<div role="button">Company</div>` hat
  den Namen Company.
- `<select name="countryCode">` hat keinen Namen. Das name-Attribut ist für
  Computer. Daher sollte das Select ein aria-label bekommen.
- <select aria-label="Country calling code" name="countryCode">…</select>
- Aus [https://www.w3schools.com/accessibility/accessibility_role_name_value.php](https://www.w3schools.com/accessibility/accessibility_role_name_value.php)
-
- Außerdem sollte custom Elemente ein Value haben. Bspw. Akkordion kann offen oder geschlossen
  sein.
- `<div role="button" aria-expanded="false"> When do I get charged for a ride?</div>`
- Aus <[https://www.w3schools.com/accessibility/accessibility_role_name_value.php](https://www.w3schools.com/accessibility/accessibility_role_name_value.php)>
-
- Nicht allein auf Farben verlassen. (Farbenblinde) Links sollten unterstrichen bleiben
- Dekorative vs. Bedeutsame Bilder
	- Dekoarative Bilder können von der Website entfernt werden ohne Auswirkungen. Sollten leeres
	  alt-Attribut haben oder als css backgrond image gesetzt sein
	- Icon fonts --> role="img" und aria-hidden="true"
	- Inline-svgs <svg aria-hidden="true">
-
	- Alt-Texte sollten am besten die Funktion des Bildes beschreiben "Home of norelem"
	- Hintergrundbilder, svgs und fonts --> role="img" aria-label="*Beschreibender
	  Text*"
-
- Link states sollten klar unterscheidbar, gut lesbar sein und hohen Kontrast haben.
- Links sollten aussagekräftig sein. Google preferiert aussagekräftige Linktexte.
- Visual Focus niemals entfernen.
-
- Skip Links:
	- Erstes element das gefocust wird erscheint ein link zum Hauptcontent: siehe Amazon
-
- Forms: Inputs die Pflichtfelder beschreiben sollten neben required attribute auch
  aria-required="true" haben
- Inputs ohne label sollten aria-label="Beschriebung" haben
- Kontrollgruppen sollten aus <fieldset> und <legend> bestehen
- ```htmlmixed
  <fieldset>
    <legend>Your date of birth</legend>
    <label for="dobDay">Day</label>
    <select id="dobDay">…</select>
    <label for="dobMonth">Month</label>
    <select id="dobMonth">…</select>
    <label for="dobYear">Year</label>
    <input id="dobYear" type="text" placeholder="YYYY">
  </fieldset>
  ```
- Aus [https://www.w3schools.com/accessibility/accessibility_labels.php](https://www.w3schools.com/accessibility/accessibility_labels.php)
-
- Autocomplete von Feldern einrichten:
- <input id="email" **autocomplete="email"** name="email"
  aria-required="true" placeholder="Email" required>
- <select id="dobDay" **autocomplete="bday-day"** aria-required="true" required>
- <select id="dobMonth" **autocomplete="bday-month"** aria-required="true" required>
- <input id="dobYear" **autocomplete="bday-year"** placeholder="YYYY"
  aria-required="true" required>
- Aus [https://www.w3schools.com/accessibility/accessibility_autocomplete.php](https://www.w3schools.com/accessibility/accessibility_autocomplete.php)
-
- Associated with the form control
- But what about the code?
- <input name="firstName"
  id="firstNameInput" type="text"
  pattern="[^.]*?">
- <p id="firstName-length-error"
  role="alert">Your first name must have at least two letters and no unusual characters</p>
- The error has the role alert. This is good. It would make a screen reader read out the content, even though it is not in focus.
- The error message is not assosiated with the field. This can be done using the aria-describedby attribute. The value is the ID of the error message.
- Also, we should add aria-invalid="true" on the invalid form control to tell screen readers that the form control has failed. An improved version of the input field:
- <input name="firstName"
  id="firstNameInput" type="text"
  pattern="[^.]*?" **aria-describedby="firstName-length-error"
  aria-invalid="true"**>
- Aus [https://www.w3schools.com/accessibility/accessibility_errors.php](https://www.w3schools.com/accessibility/accessibility_errors.php)