### Mediator
Наприклад в додатках де працюємо з сокетами Медіатором виступає наш сервер, який зв'язує різних клієнтів, приклад використання:
```javascript
const onlineUsers = new Map();

io.on('connection', (socket) => {
  const sendUsersInRoomIds = (roomId) => {
    const users = [];

    io.sockets.adapter.rooms.get(roomId).forEach((socketId) => {
      users.push(onlineUsers.get(socketId));
    });

    socket.to(roomId).emit(socketEvents.usersOnlineInfo, users);
  };

  socket.on(socketEvents.join, ({ roomId, userId }) => {
    socket.rooms.forEach((room) => socket.leave(room));
    socket.join(roomId);
    onlineUsers.set(socket.id, userId);

    sendUsersInRoomIds(roomId);
  });

  socket.on(socketEvents.send, (data) => {
    socket.to(data.chat_id).emit(socketEvents.receive, data);
  });

  socket.on('disconnecting', () => {
    onlineUsers.delete(socket.id);

    socket.rooms.forEach((roomId) => {
      sendUsersInRoomIds(roomId);
    });
  });
});
```
