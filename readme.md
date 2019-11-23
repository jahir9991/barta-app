# barta-app

endpoint : http://api.zeeat.com/api/v1/

    AUDIO_MESSAGE_ENDPOINT: 'https://api.zeeat.com/static/voice_message/',
    PICTURE_MESSAGE_ENDPOINT: 'https://api.zeeat.com/static/picture_message/',
    IMAGE_ENDPOINT: 'https://api.zeeat.com/static/images/', (like avatar)

    schema info : http://api.zeeat.com/api/v1/{table name}/info

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
   
   
# All
        

    user: http://api.zeeat.com/api/v1/users
    barta: http://api.zeeat.com/api/v1/bartas
    barta answer: http://api.zeeat.com/api/v1/bartaanswers
    query(prosno): http://api.zeeat.com/api/v1/queries
    query answer : http://api.zeeat.com/api/v1/queryanswers

    fcm token:  http://api.zeeat.com/api/v1/fcmtokens
