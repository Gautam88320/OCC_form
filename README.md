# OCC Student reg form
  
<html>

<head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/knockout/3.5.1/knockout-latest.js"></script>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FORM DATA</title>
    <style>
        *{ box-sizing: border-box; }
        
    </style>
</head>
<body>
    
    <div class="container">
        <h2>Student Registration Form</h2>
        <form role="form" onsubmit="signUp(event);">
            <div class="form-group">
               First Name <input type="text" name="fname" id="fname" data-bind="value:firstName" placeholder="First Name" required>
            </div>
            <div class="form-group">
                Last Name<input type="text" name="lname" id="lname"  data-bind="value:lastName" placeholder="Last Name" required>
            </div>
			<div class="form-group">
              Date of birth  <input type="dob" name="dob" id="dob" data-bind="value:dob" required>
            </div>
            <div class="form-group">
               Email <input type="email" name="email" id="email"  required>
            </div>
			<div class="form-group">
               Mobile <input type="mobile" name="mobile" id="mobile"  required>
            </div>
		Gender<input type="radio" name="gender" id="gender" data-bind="value:male" >Male
             <input type="radio" name="gender"  id="gender" data-bind="value:female">Female

			 <div class="form-group">
               Address<input type="address" name="address" id="address"  required>
            </div>
			<div class="form-group">
               City<input type="city" name="city" id="city"  required>
            </div>
			<div class="form-group">
              zip Code <input type="zip" name="zip" id="zip"  required>
            </div>
			
			<label>State:</label>
                <select class="country">
                    <option>Select</option>
                    <option value="usa">Texas</option>
                    <option value="india">Uttar Pradesh</option>
                    <option value="uk">England</option>
                </select>
			</div>
			<div class="form-group">
			<label>Country:</label>
                <select class="country">
                    <option>Select</option>
                    <option value="usa">United States</option>
                    <option value="india">India</option>
                    <option value="uk">United Kingdom</option>
                </select>
			</div>
			
		Hobby
      <input type="checkbox" name="Singing" value="Singing" /> Singing 
      <input type="checkbox" name="Drawing" value="Drawing" /> Drawing
      <input type="checkbox" name="Dancing" value="Dancing" /> Dancing <br />
      <input type="checkbox" name="other" value="other" /> Other <input type="text"><br/>
	  
	  Course applied<input type="radio" name="bca" data-bind="value:bca" >BCA
             <input type="radio" name="bsc" data-bind="value:bsc">BSC
			  <input type="radio" name="bcom" data-bind="value:bcom">BCOM
			   <input type="radio" name="ba" data-bind="value:ba">BA<br/>
			
            <div class="form-group">
                <button type="submit">Get data</button>
            </div>
        </form>

        <h2>Data from Local Storage</h2>
        <div id="output">
            <!-- DISPLAY USERS DATA -->
        </div>
    </div>

    <script type="text/javascript">
        const signUp = e => {
            let formData = {
                fname: document.getElementById('fname').value,
                lname: document.getElementById('lname').value,
				dob:document.getElementById('dob').value,
                email: document.getElementById('email').value,
                mobile: document.getElementById('mobile').value,
			    gender: document.getElementById('gender').value,
				address:document.getElementById('address').value,
				city:document.getElementById('city').value,
				zip:document.getElementById('zip').value,
				state:document.getElementById('state').value
            }
            localStorage.setItem('formData', JSON.stringify(formData));
            // console.log(localStorage.getItem('formData'));
            dispData();
            e.preventDefault();
        }

        function dispData(){
            // console.log(localStorage.getItem('formData'));
            let {fname, lname, dob, email, mobile, gender, address, city, zip, state} = JSON.parse(localStorage.getItem('formData'));
            var output = document.getElementById('output');
            output.innerHTML = `
            <table>
                <tbody>
                    <tr>
                        <td>First Name</td>
                        <td>${fname}</td>
                    </tr>
                    <tr>
                        <td>Last Name</td>
                        <td>${lname}</td>
                    </tr>
					<tr>
                        <td>Date Of Birth</td>
                        <td>${dob}</td>
                    </tr>
                    <tr>
                        <td>Email Address</td>
                        <td>${email}</td>
                    </tr>
                    <tr>
                        <td>Mobile</td>
                        <td>${mobile}</td>
                    </tr>
					<tr>
                        <td>Gender</td>
                        <td>${gender}</td>
                    </tr>
					<tr>
                        <td>Address</td>
                        <td>${address}</td>
                    </tr>
					<tr>
                        <td>City</td>
                        <td>${city}</td>
                    </tr>
					<tr>
                        <td>Zip</td>
                        <td>${zip}</td>
                    </tr>
					<tr> 
                        <td>State</td>
                        <td>${state}</td>
                    </tr>
                </tbody>
            </table>`;
        }
        dispData();
		
		function viewModel(){
	this.firstName=ko.observable("Hritik"),
	this.lastName=ko.observable("Roshan");
	
	}
	
	ko.applyBindings(new  viewModel);
		
    </script>
</body>
</html>
