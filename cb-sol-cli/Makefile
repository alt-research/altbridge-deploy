SOL_URL=git@github.com:alt-research/altbridge-solidity.git
SOL_VERSION="v2.0.0-alt"

fetch-contracts:
	@echo " > \033[32mFetching chainbridge-solidity contracts... \033[0m "
	git clone ${SOL_URL} chainbridge-solidity && cd chainbridge-solidity && git checkout ${SOL_VERSION}

compile:
	cd chainbridge-solidity && npm install && npx truffle compile

install: fetch-contracts compile
	@echo " > \033[32mInstalling cb-sol-cli... \033[0m "
	npm link .

clean:
	rm -rf chainbridge-solidity/
