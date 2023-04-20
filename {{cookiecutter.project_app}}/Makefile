
clean:
	@find . -name "*.pyc" -exec rm -rf {} \;
	@find . -name "__pycache__" -delete

run-dev:
	@echo 'Running local development'
	docker-compose up -d --remove-orphans
	npm run dev &
	python manage.py runserver

run-tests:
	@echo 'Checking for migrations'
	python manage.py makemigrations --dry-run --check
	pytest
