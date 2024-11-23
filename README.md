# Django_requirements

1. **Crear el ambiente, de preferencia con python 3.8:**
    ```bash
    python -m venv django_venv

    django_venv\Scripts\activate
    ```

2. **Instalar django en su ambiente virtual**
    ```
    pip install django
    ```


3. **Crear un proyecto con Django:**
    ```bash
    django-admin startproject Django_template
    cd Django_template
    ```
    

4.  **Crear una app, puede tener el nombre que gustes:**
    ```bash
    python manage.py startapp tasks
    ```



## Añadir los templates en HTML

1. **Crear el archivo`task/templates/tasks/task_list.html` y añade el siguiente código:**
    ```
      <!DOCTYPE html>
      <html lang="en">
      <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
    </head>
    <body>
    <h1>To-Do List</h1>
    <a href="{% url 'add_task' %}">Add Task</a>
    <ul>
        {% for task in tasks %}
            <li>
                {{ task.title }} - 
                {% if task.completed %}
                    Completed
                {% else %}
                    Not Completed
                {% endif %}
                <a href="{% url 'edit_task' task.pk %}">Edit</a>
            </li>
        {% endfor %}
    </ul>
    </body>
    </html>

    ```

2. **Crear el archivo`task/templates/tasks/task_form.html` y añade el siguiente código:**
    ```
      <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Task Form</title>
    </head>
    <body>
    <h1>{% if form.instance.pk %}Edit Task{% else %}Add Task{% endif %}</h1>
    <form method="POST">
        {% csrf_token %}
        {{ form.as_p }}
        <button type="submit">Save</button>
    </form>
    <a href="{% url 'task_list' %}">Back to List</a>
    </body>
    </html>

    ```

3. **Crear el archivo`task/templates/registration/login.html` y añade el siguiente código:**
    ```
   <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login</title>
    </head>
    <body>
    <h1>Login</h1>
    <form method="POST">
        {% csrf_token %}
        {{ form.as_p }}
        <button type="submit">Login</button>
    </form>
    </body>
    </html>


    ```



