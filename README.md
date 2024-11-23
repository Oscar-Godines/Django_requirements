# Django_requirements

1. **Crear el ambiente, de preferencia con python 3.8 o más reciente:**
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
        <div class="card shadow">
        <div class="card-header bg-success text-white">
            <h1 class="h3">To-Do List</h1>
        </div>
        <div class="card-body">
            <a href="{% url 'add_task' %}" class="btn btn-primary mb-3">+ Add Task</a>
            <ul class="list-group">
                {% for task in tasks %}
                    <li class="list-group-item d-flex justify-content-between align-items-start">
                        <div>
                            <strong>{{ task.title }}</strong>
                            <p>{{ task.description }}</p>
                            <small>Priority: {{ task.priority }}</small><br>
                            <small>Due: {{ task.due_date|date:"M d, Y" }}</small>
                        </div>
                        <div>
                            {% if task.completed %}
                                <span class="badge bg-success">Completed</span>
                            {% else %}
                                <span class="badge bg-warning text-dark">Pending</span>
                            {% endif %}
                            <a href="{% url 'edit_task' task.pk %}" class="btn btn-sm btn-warning mt-2">Edit</a>
                        </div>
                    </li>
                {% endfor %}
            </ul>
        </div>
    </div>
    <form action="{% url 'logout' %}" method="post" style="display: inline;">
    {% csrf_token %}
    <button type="submit">Logout</button>
    </form>
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
    <div class="d-flex justify-content-center align-items-center vh-100">
        <div class="card shadow" style="width: 30rem;">
            <div class="card-header bg-primary text-white">
                <h2 class="h5">{% if form.instance.pk %}Edit Task{% else %}Add Task{% endif %}</h2>
            </div>
            <div class="card-body">
                <form method="POST">
                    {% csrf_token %}
                    {{ form.as_p }}
                    <button type="submit" class="btn btn-primary w-100">Save</button>
                </form>
                <a href="{% url 'task_list' %}" class="btn btn-link text-secondary mt-3">Back to List</a>
            </div>
        </div>
    </div>
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



