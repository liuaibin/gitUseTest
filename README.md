# Installation

## Install via Package Management Tool
To install Jsonnet, you can follow these steps:
'''bash
sudo apt-get update
sudo apt-get install jsonnet=0.20.0
'''
## Install via Code
'''bash
git clone --branch v0.20.0 https://github.com/google/jsonnet.git
cd jsonnet
make
cp jsonnet /usr/bin
'''

# Generating Grafana Dashboard JSON
To generate Grafana dashboard JSON, you can use the following command:
'''bash
./build.sh -c '{dashboard_name}' -o 'output_json_path'

# Example:
./build.sh -c 'all' -o out # Generate all dashboards
./build.sh -c 'overview' -o out # Generate the overview dashboard
'''

# Additional Resources

- [Grafonnet API Documentation](https://github.com/grafana/grafonnet/tree/main/gen/grafonnet-v9.5.0/docs)

- [Wiki](https://wiki.finalfrontier.cn/pages/viewpage.action?pageId=507543678)
