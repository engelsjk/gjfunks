# gjfunks

*Experimental!* A small library and suite of tools for manipulating GeoJSON files.

## gjsplit

Splits a GeoJSON FeatureCollection file up into many separate GeoJSON Features files.

```bash
go get github.com/engelsjk/gjfunks/cmd/gjsplit
```

* Fix polygon windings to match RFC 7946 S3.1.6 specification. 
* Use custom names or unique key-values from GeoJSON properties for output file prefixes.

```bash
usage: gjsplit [<flags>] [<input>]

Flags:
      --help              Show context-sensitive help (also try --help-long and --help-man).
  -o, --output=""         output dir
      --stdout            print to stdout only
      --keeponlykey=""    keep only this feature property key
      --outkey=""         feature property key-value for output file prefixes
      --outprefix=""      output file prefix
      --flat              flat file
      --fixtospec         fix polygon/multipolygon features to meet RFC7946 S3.1.6
  -d, --dryrun            no output files saved

Args:
  [<input>]  input file
``` 

## gjbuild

Builds a file of a GeoJSON Feature Collection (or new-line delimited GeoJSON Features) from a directory containing many separate files of GeoJSON Features or Feature Collections.

```bash
go get github.com/engelsjk/gjfunks/cmd/gjbuild
```

* Filter out Features with duplicate key-value properties.
* Keep only specified Feature properties if needed.
* Output as either a GeoJSON Feature Collection or new-line delimited GeoJSON Features.
* Fix polygon windings to meet RFC 7946 S3.1.6. specification.

```bash
usage: gjbuild [<flags>] [<input>]

Flags:
      --help              Show context-sensitive help (also try --help-long and --help-man).
  -o, --output=""         output filepath
      --filterkey=""      feature property key to filter duplicate values
      --keeponlykey=""    keep only this feature property key
      --ndjson            output as newline-delimited json
      --fixtospec         fix polygon/multipolygon features to meet RFC7946 S3.1.6
      --overwrite         overwrite existing output file

Args:
  [<input>]  input path
```

## ToDo

* Add tests
* Compare performance benchmarks to different size GeoJSON files
* gjsplit
  * Add progress bar?
  * Output warning about how many features did not have out-key property
