# barta-app

endpoint : http://api.zeeat.com/api/v1/

    ASSET ENDPOINT : 'https://api.zeeat.com/static/all_assets/',
   

    schema info : http://api.zeeat.com/api/v1/{table name}/info
    
# Area

    area: http://api.zeeat.com/api/v1/areas
    
# Auth
    login:   post::  http://api.zeeat.com/api/v1/auth/login  param::{phone: string,password :string }
    signout: post::  http://api.zeeat.com/api/v1/auth/signOut  param:: { fcm_token: string }

# token
    post::  http://api.zeeat.com/api/v1/fcmtokens   param::{user_id: number; fcm_token: string}
    
# Area     
    get all divisions:   http://api.zeeat.com/api/v1/areas?limit=all&type_id=4
    only for sylhet :    http://api.zeeat.com/api/v1/areas?limit=all&type_id=4&id=67
    alldistrictof_sylhet http://api.zeeat.com/api/v1/areas?limit=all&type_id=5parent_id=67 
    for upazilla         http://api.zeeat.com/api/v1/areas?limit=all&type_id=6parent_id=***

# barta 
   create new barta 
   post::  http://api.zeeat.com/api/v1/bartas
    form::
    
        let selectAll = '';
	let parent_id_list = [];
	let officer_id_list = [];
       if (this.selectAllDivision) {
			selectAll = 'division';
		}
        else if (this.selectAllDistrict) {
			selectAll = 'district';
			const divisionIdList = this.selectedDivision.map(item => item.id);
			parent_id_list = divisionIdList;
		} 
        else if (this.selectAllUpazilla) {
			selectAll = 'upazilla';
			const districtIdList = this.selectedDistrict.map(item => item.id);
			parent_id_list = districtIdList;
		}
        else if (this.selectAllOfficer) {
			selectAll = 'officer';
			const upazillaIdList = this.selectedUpazilla.map(item => item.id);
			parent_id_list = upazillaIdList;
		} 
        else {
			officer_id_list = this.selectedOfficer.map(item => item.id);
		}
        mydata.append('status', '1');
		mydata.append('select_all', selectAll);
		mydata.append('parent_id_list', JSON.stringify(parent_id_list));
		mydata.append('officer_id_list', JSON.stringify(officer_id_list));
   
  get all officer by upazilla id:
  
  	  http://api.zeeat.com/api/v1/users?limit=all&role=officer&upazilla_id=[2968,99]
	  
	  
	
# Barta answer
	get by id::           http://api.zeeat.com/api/v1/bartaanswers/{id}
	get by receiver_id::  http://api.zeeat.com/api/v1/bartaanswers?receiver_id=10
	
   	update :: put::       http://api.zeeat.com/api/v1/bartaanswers/{id} 
			      param:: { answer_body:'....'}
	
# Query  
	http://api.zeeat.com/api/v1/queries
	
	create new query::  post:: http://api.zeeat.com/api/v1/queries  
			   param::      {	sender_id:1,
						message_type:'NORMAL',
						message_title:'any',
						message_body:'...',
						status:1,
						select_all:'officer', //same logic like barta
						parent_id_list:'[9,9]',//...
						officer_id_list:'[9,9]',//...
						question_list:'[{"question":"কিভাবে জেলার মান উন্নয়ন করা সম্ভব? ","answer":null},
								{"question":"কিভাবে জেলার মান উন্নয়ন করা সম্ভব? ","answer":null}
							       ]'
					 } 
 # Query answer
 		http://api.zeeat.com/api/v1/queryanswers
	get by id::           http://api.zeeat.com/api/v1/queryanswers/{id}
	get by receiver_id::  http://api.zeeat.com/api/v1/queryanswers?receiver_id=10
	update :: put::       http://api.zeeat.com/api/v1/queryanswers/{id} 
			      param:: { answer_list: '[{"question":"ghh","answer":"জরুরি "}]' }
 
# profile update 
	 put   https://api.zeeat.com/api/v1/users/{id}
	 param::	{ address: "1"
			email: "jahir@gmail.com"
			name: "abc"
			phone: "111111"}
 # password update
 	post   https://api.zeeat.com/api/v1/auth/passwordchange
	param::  {     id: 9 //userid
			new_password: "aaaa"
			old_password: "aaaa"
		 }
# avatar update
 	put   https://api.zeeat.com/api/v1/users/{id}
	param::	{ avatar: file}


# All
        

    user: http://api.zeeat.com/api/v1/users
    barta: http://api.zeeat.com/api/v1/bartas
    barta answer: http://api.zeeat.com/api/v1/bartaanswers
    query(prosno): http://api.zeeat.com/api/v1/queries
    query answer : http://api.zeeat.com/api/v1/queryanswers

    fcm token:  http://api.zeeat.com/api/v1/fcmtokens
