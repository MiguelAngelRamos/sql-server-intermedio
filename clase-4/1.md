```sql
-- LIKE
select * from users;

-- Filtrar con LIKE  y luego contrar los registros de first_name que comienzen con "J"
SELECT COUNT(*) AS total_users_with_J FROM users WHERE first_name LIKE 'J%';

-- Combinar LIKE con 'AND' 

SELECT first_name, last_name, email FROM users WHERE email LIKE '%@google.com' AND first_name LIKE 'H%';

-- Usar Like con ORDER BY
SELECT first_name, last_name FROM users WHERE last_name LIKE '%son%' ORDER BY first_name asc;

-- Agrupa por pais y calcula el promedio de seguidores (followers) en cada pais. Luego los paises se orden de mayor a menor segun promedio
SELECT country, AVG(followers) as avg_followers FROM users GROUP BY country ORDER BY avg_followers DESC;

SELECT following, COUNT(*) AS user_count FROM users GROUP BY following ORDER BY user_count DESC;

-- OBTENER LOS USUARIOS QUE TIENEN MAS SEGUIDORES QUE EL PROMEDIO >
SELECT AVG(followers) FROM users;

SELECT first_name, last_name, followers FROM users WHERE followers > (SELECT AVG(followers) FROM users);

```