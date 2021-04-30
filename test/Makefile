all:
	cc -g -fPIC -shared -Wl,-soname,libdemo.so.1 -o libdemo.so.1.0.1 libdemo.c
	ln -sf libdemo.so.1.0.1 libdemo.so.1
	ln -sf libdemo.so.1 libdemo.so
	cc -g -o app app.c -L. -ldemo
	LD_LIBRARY_PATH=. ldd app
test:
	rm -rf ./prof_data
	mkdir -p ./prof_data
	LD_PROFILE=libdemo.so.1 LD_PROFILE_OUTPUT=${shell pwd}/prof_data && ls ./prof_data && LD_LIBRARY_PATH=. ./app
	sudo /opt/glibc/bin/sprof -p ./libdemo.so.1 ./prof_data/libdemo.so.1.profile
	sudo /opt/glibc/bin/sprof -q ./libdemo.so.1 ./prof_data/libdemo.so.1.profile
	sudo /opt/glibc/bin/sprof -c ./libdemo.so.1 ./prof_data/libdemo.so.1.profile
