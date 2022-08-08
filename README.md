# get-yaml-value
This GitHub Action returns a list of YAML file values

## Usage
```yaml
    - uses: rmeneely/get-yaml-value@v1
      with:
        # Infile. The YAML file to be read
        # Default: 'values.yaml'
        # Optional
        infile: 'values.yaml
        # varlist - a comma separated list of variables. e.g version,image.tag
        # Default: ''
        # Required
        varlist: ''
```

## Examples
```yaml
    # Returns the image tag in values.yaml file
    # Example: 
    - uses: rmeneely/get-yaml-value@v1
      with:
        infile: values.yaml
        varlist: 'image.tag'
```

```yaml
    # Returns the appVersion and version in Chart.yaml
    # Example: 
    - uses: rmeneely/get-yaml-value@v1
      with:
        infile: Chart.yaml
        varlist: appVersion,version
```

```yaml
    # Returns a dependency version in Chart.yaml from within a list of dependencies
    # Example: 
    - uses: rmeneely/get-yaml-value@v1
      with:
        infile: Chart.yaml
        varlist: dependencies[name=myapp].version"
```

This will return the `dependencies.version` where that same list item has `dependencies.name` set to 'myapp'.
Caveat: Does not support multiple variable[condition].variable formats within the same query


## Output
```shell
steps.get-yaml-value.outputs.values - Set to comma separated list of <variable>=<value>
```

## License
The MIT License (MIT)
