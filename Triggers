trigger ExpirationAlert on Food_Donation__c (before insert, before update) {
    for (Food_Donation__c donation : Trigger.new) {
        Integer daysUntilExpiration = donation.Expiration_Date__c.daysBetween(Date.today());
        if (daysUntilExpiration <= 3) {
            Messaging.SingleEmailMessage mail = new Messaging.SingleEmailMessage();
            mail.setToAddresses(new String[] {'goldchat59@gmail.com'});
            mail.setSubject('Urgent: Food Donation Expiring Soon');
            mail.setPlainTextBody('A food donation is expiring in ' + daysUntilExpiration + ' days.');
            Messaging.sendEmail(new Messaging.SingleEmailMessage[] { mail });
        }
    }
}
