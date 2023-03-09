init_git:
	@echo "Initialize git..."
	git init 

install: 
	@echo "Installing..."
	# Initialize poetry
	poetry install
	# Pre-commit is a framework for building and running git hooks
	poetry run pre-commit install

create_repo:
	@echo "Creating repo..."
	# Create a repo named after the project
	gh repo create {{cookiecutter.project_name}} --{{cookiecutter.repository}}

first_commit:
	@echo "First commit..."
	# Initialize git and push the first commit
	git add .
	git commit -m ":rocket: initial commit!"
	git branch -M develop
	git remote add origin git@github.com:ChiaraGitHub/{{cookiecutter.project_name}}.git
	git push -u origin develop

init: init_git install create_repo first_commit

active:
	@echo "Activating virtual environment"
	poetry shell

test:
	@echo "Run tests..."
	pytest

docs:
	@echo "View API documentation..."
	PYTHONPATH={{cookiecutter.project_name}} pdoc {{cookiecutter.project_name}} --http localhost:8080

docs_save:
	@echo Save documentation to docs... 
	PYTHONPATH={{cookiecutter.project_name}} pdoc {{cookiecutter.project_name}} -o docs

