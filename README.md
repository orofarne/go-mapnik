go-mapnik
=========

Go bindings for mapnik (http://www.mapnik.org or
http://github.com/mapnik/mapnik)

These bindings rely on http://github.com/springmeyer/mapnik-c-api.

Installation
-----------

### Linux / MacOS

1. Install Mapnik build environmnent,
	- e.g. Ubuntu: `apt-get install libmapnik-dev`
2. Download the sources, either by
    - `git clone` the repository to $GOPATH/src/orofarne/go-mapnik

	OR

    - `go get -d github.com/orofarne/go-mapnik`
3. `cd go-mapnik` and run `cmake . && make && go test`.
   That script will setup the correct paths for including Mapnik headers and
   linking against the Mapnik shared library, as well as download the Mapnik C
   API source and `go install` the bindings.

Usage
-----


