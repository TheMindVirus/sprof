TEST_LIBS+=libbcm_host.so
TEST_LIBS+=libbrcmEGL.so
TEST_LIBS+=libbrcmGLESv2.so

all:
	gcc ./main.c -o ./app -g -pg -I /opt/vc/include/ -L /opt/vc/lib/ -lbcm_host -lbrcmEGL -lbrcmGLESv2
test:
	rm -rf ./prof_data
	mkdir -p ./prof_data
	cd ./prof_data && ../app && gprof ../app -l -z > ./app.log
	for TEST_LIB in $(TEST_LIBS); do \
		LD_PROFILE=$$TEST_LIB \
		LD_PROFILE_OUTPUT=./prof_data \
		LD_LIBRARY_PATH=/opt/vc/lib/ ./app ;\
		sudo LD_LIBRARY_PATH=/opt/vc/lib/ /opt/glibc/bin/sprof -p $$TEST_LIB ./prof_data/$$TEST_LIB.profile > ./prof_data/$$TEST_LIB.p.log ;\
		sudo LD_LIBRARY_PATH=/opt/vc/lib/ /opt/glibc/bin/sprof -q $$TEST_LIB ./prof_data/$$TEST_LIB.profile > ./prof_data/$$TEST_LIB.q.log ;\
		sudo LD_LIBRARY_PATH=/opt/vc/lib/ /opt/glibc/bin/sprof -c $$TEST_LIB ./prof_data/$$TEST_LIB.profile > ./prof_data/$$TEST_LIB.c.log ;\
	done
	rm -f ./gmon.out
clean:
	rm -f ./app
