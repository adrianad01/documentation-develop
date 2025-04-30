# WINDOWS COMMANDS

1. Verificar si un puerto está en uso

```
netstat -ano | findstr :<Port>
```

2. Eliminar el uso de ese puerto

```
taskkill /PID <Puerto> /F
```