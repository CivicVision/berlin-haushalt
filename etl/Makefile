GENERATED_FILES = bezirke.geojson
BEZDIR = bezirke
.PHONY: all clean

all: $(GENERATED_FILES)

clean:
	rm -Rf data/* && rm -Rf $(BEZDIR)

.INTERMEDIATE: bezirke.zip
bezirke.zip:
	curl -o $@ "https://www.statistik-berlin-brandenburg.de/opendata/RBS_OD_BEZ_1412.zip"

$(BEZDIR): bezirke.zip
	unzip $< -d $@

bezirke.geojson: $(BEZDIR)
	ogr2ogr -f GeoJSON -t_srs crs:84 data/$@ $</*.shp
