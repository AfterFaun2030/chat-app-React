Question 1:
App.js: Récupère les fonctions de Join.js et Chat.js ainsi que le css de App.css pour afficher l'application et consolider les fonctions pour avoir une app utilisable.

Chat.js: Gère l'affichage de la page chatroom et interprète les actions de l'utilisateur. Utilise les fonctions de Message.js, Sidebar.js et SocketContext.js.

Message.js: Contient la fonction Message, détermine l'autheur entre System, Le client(own) et un autre utilisateur(other) et affiche le message en conséquence.

Sidebar.js: Contient la fonction Sidebar, affiche les utilisateurs dans un chatroom.

Join.js: Gère les fonctions pour rejoindre ou créer une room, récupère la liste de room exhistante et utilise les fonctions de SocketContext.js.

server.js: Démarre le serveur, reçoit les actions des utilisateurs et effectue les modifications nécessaires.

SocketContext.js: Gère la communication entre le client et le serveur en temps réel.

Question 2:

a) •	Comment le socket est créé et partagé entre tous les composants React (indice : SocketContext.js). 

Le socket est créé dans socketcontext.js par la fonction io() et est sauvegarder dans la constante socket. Les composantes peuvent ensuite y accéder en important SocketContext.js et en fesant appel à usesocket().

b) •	Quel évènement Socket.io est émis quand un utilisateur rejoint une room, et ce qui se passe cote serveur.

L'évènement join_room est émis avec les infos username et room. Le serveur s'assure que toutes les données sont légitime, ensuite, il envoit un message indiquant la connection de l'utilisateur un chatroom et modifie la liste de participant.

c) •	Comment les messages sont diffusés à tous les membres d'une room (emit vs broadcast).

L'utilisateur envoit un message au serveur (socket.emit("send_message", messageData);) contenant les donnés d'utilisateur, room, message et date. Le serveur reçoit les donnés et les envoits à la chatroom (io.to(data.room).emit("receive_message", data);) et chat.js reçoit les data et l'affiche selon l'expéditeur du message.