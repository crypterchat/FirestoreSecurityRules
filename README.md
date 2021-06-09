# FirestoreSecurityRules

rules_version = '2';
service cloud.firestore {
match /databases/{database}/documents {
match /{document=\*\*} {
allow read, write: if request.auth!=null;
allow read, write: if request.auth==null;

    }
     match /version/userapp {

allow read, write : if request.auth!=null;
allow read, write : if request.auth==null;
}

match /users/{userId} {
allow read, write : if request.auth.uid== userId ;
}
}

}
