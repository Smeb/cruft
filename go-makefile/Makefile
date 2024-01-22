GOLINT_CMD=golangci-lint
GO_FILES=$(shell find . -type f -regex ".*go")

define check_linter
 	@if ! command -v $(GOLINT_CMD) > /dev/null; then\
   		echo "$(GOLINT_CMD) must be installed to run linting: try brew install $(GOLINT_CMD)";\
   		exit 1;\
   	fi
endef

lint: .golangci.yml ## Lints the code

fix: ## Fixes any issues found during linting
	@$(call check_linter)
	$(GOLINT_CMD) run --fix

.golangci.yml: $(GO_FILES)
	@$(call check_linter)
	$(GOLINT_CMD) version
	$(GOLINT_CMD) run
	touch .golangci.yml
