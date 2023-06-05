
clean:
	@find . -name "*.pyc" -exec rm -rf {} \;
	@find . -name "__pycache__" -delete

run-dev:
	@echo 'Running local development'
	docker-compose -f docker/docker-compose.yaml up -d  --remove-orphans
	npm run dev &
	python manage.py runserver

run-prod:
	@echo 'Running local development'
	docker-compose -f docker/docker-compose.yaml -f docker/docker-compose-deploy.yaml up -d  --remove-orphans

stop-prod:
	docker-compose -f docker/docker-compose.yaml -f docker/docker-compose-redis.yaml -f docker/docker-compose-deploy.yaml stop

run-tests:
	@echo 'Checking for migrations'
	python manage.py makemigrations --dry-run --check
	pytest

build-prod:
	@echo 'Building production image'
	docker-compose -f docker/docker-compose.yaml -f docker/docker-compose-deploy.yaml build

update-requirements:
	pip install -U -q pip-tools
	pip-compile --generate-hashes --resolver=backtracking -o requirements/base/base.txt pyproject.toml
	pip-compile --generate-hashes --resolver=backtracking --extra dev -o requirements/dev/dev.txt pyproject.toml
	pip-compile --generate-hashes --resolver=backtracking --extra tools -o requirements/optional/optional.txt pyproject.toml
	pip-compile --generate-hashes --resolver=backtracking --extra deploy -o requirements/deploy/deploy.txt pyproject.toml

install-dev:
	@echo 'Installing pip-tools...'
	export PIP_REQUIRE_VIRTUALENV=true; \
	pip install -U -q pip-tools
	@echo 'Installing requirements...'
	pip-sync requirements/base/base.txt requirements/dev/dev.txt

install-dev-optional:
	@echo 'Installing pip-tools...'
	export PIP_REQUIRE_VIRTUALENV=true; \
	pip install -U -q pip-tools
	@echo 'Installing requirements...'
	pip-sync requirements/base/base.txt requirements/dev/dev.txt requirements/optional/optional.txt

setup:
	@echo 'Setting up the environment...'
	pip config --site set global.extra-index-url https://pypi.ehps.ncsu.edu/
	make install-dev