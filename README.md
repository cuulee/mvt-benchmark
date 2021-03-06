MVT Benchmark
=============

Benchmark for MVT vector tile creation and delivery from a PostGIS database.

The benchmark uses the `natural-earth-quickstart` style from the Tegola web demo as target style.

Measurement targets:
* How long does it take to generate all tiles (single node / multiple nodes)
* How many requests/s does the tile server deliver in web server mode (with and without tile cache)

DB Setup
--------

Data: NaturalEarth 4.1 ([Site](http://www.naturalearthdata.com/) / [Github](https://github.com/nvkelso/natural-earth-vector)) is used as test data.

    # Set Postgresql environment variables when needed: PGHOST, PGPORT, PGUSER, PGPASSWORD
    cd data
    make
    make db

Run benchmark
-------------

    cd t-rex
    make clean seed_region stats
    make clean seed_region_4 stats

Http test:

    t_rex serve mvtbench.toml
    make http
