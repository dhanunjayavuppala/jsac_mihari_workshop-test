# Vs. ProjectDiscovery or How I Learned to Stop Worrying and Love It

<figure markdown>
  ![img](https://i.imgflip.com/8bqf7d.jpg){: style="width:480px"}
</figure>

## What Are Uncover and Nuclei?

- [projectdiscovery/uncover](https://github.com/projectdiscovery/uncover)
  - Quickly discover exposed hosts on the internet using multiple search engines.
- [projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei)
  - Fast and customizable vulnerability scanner based on simple YAML based DSL.

## A Key Difference

- Mihari is a **passive** monitoring tool.
- ProjectDiscovery's Nuclei is an **active** monitoring/scanning tool.

Nuclei can validate/filter findings by scanning and Mihari cannot.

## Misc Differences

- A number of services supports:
  - Mihari supports **15+** services.
  - Uncover supports **10** services.
- Data persistence:
  - Mihari **does support** data persistence in SQL database.
  - Nuclei **does support** data persistence in LevelDB.
    - Also can create a report in Elasticsearch, Splunk, ProjectDiscovery's Cloud Platform, etc.
- Data enrichment:
  - Mihari **does have** automated data enrichment feature.
  - Nuclei & Uncover **don't have** automated data enrichment feature.

## So, So What?

<figure markdown>
  ![img](https://i0.wp.com/jtmat.co.uk/wp-content/uploads/2021/05/Picture1.jpg?resize=293%2C226&ssl=1)
</figure>

I don't know. :D

It depends on what you are trying to do. ProjectDiscovery may be more the right toolset for you.

## A Good Pairing?

<figure markdown>
  ![img](https://i.redd.it/zu1ed7d9cs521.jpg){: style="width:480px"}
</figure>

Anyway you can combine both. Collecting data in Mihari and validating it with Nuclei.

It's beneficial to save API quota because Nuclei uses API every time when Uncover options are set.

```bash
# Shodan API key is used more than twice
nuclei -uq "ip:1.1.1.1" -ue shodan ...
nuclei -uq "ip:1.1.1.1" -ue shodan ...
```

You can convert Mihari data to Nuclei's targets by using [list-transform](https://ninoseki.github.io/mihari/usage/#search-with-transformation) feature.
