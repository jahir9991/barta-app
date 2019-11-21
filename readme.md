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


        

    user: http://api.zeeat.com/api/v1/users
    barta: http://api.zeeat.com/api/v1/bartas
    barta answer: http://api.zeeat.com/api/v1/bartaanswers
    query(prosno): http://api.zeeat.com/api/v1/queries
    query answer : http://api.zeeat.com/api/v1/queryanswers

    fcm token:  http://api.zeeat.com/api/v1/fcmtokens
