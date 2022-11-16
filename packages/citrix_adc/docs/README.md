# Citrix ADC Integration

## Overview

The Citrix ADC integration allows you to monitor your Citrix ADC instance. Citrix ADC is an application delivery controller that performs application-specific traffic analysis to intelligently distribute, optimize, and secure Layer 4 - Layer 7 (L4–L7) network traffic for web applications.

Use the Citrix ADC integration to collect metrics related to the interface. Then visualize that data in Kibana, create alerts to notify you if something goes wrong, and reference logs when troubleshooting an issue.

## Data streams

The Citrix ADC integration collects metrics data.

Metrics give you insight into the statistics of the Citrix ADC. Metrics data streams collected by the Citrix ADC integration include [interface](https://developer-docs.citrix.com/projects/netscaler-nitro-api/en/12.0/statistics/network/interface/), so that the user could monitor and troubleshoot the performance of the Citrix ADC instances.

Note:
- Users can monitor and see the metrics inside the ingested documents for Citrix ADC in the logs-* index pattern from `Discover`.

## Compatibility

This integration has been tested against Citrix ADC `v13.0` and `v13.1`.

## Requirements

You need Elasticsearch for storing and searching your data and Kibana for visualizing and managing it. You can use our hosted Elasticsearch Service on Elastic Cloud, which is recommended, or self-manage the Elastic Stack on your own hardware.

In order to ingest data from Citrix ADC, you must know the host(s) and the administrator credentials for the Citrix ADC instance.

Host Configuration Format: `http[s]://host[:port]`

Example Host Configuration: `http://localhost:9080`

## Metrics reference

### Interface

This is the `interface` data stream. The Citrix ADC interfaces are numbered in slot/port notation. In addition to modifying the characteristics of individual interfaces, you can configure virtual LANs to restrict traffic to specific groups of hosts.

An example event for `interface` looks as following:

```json
{
    "@timestamp": "2022-10-07T06:24:46.588Z",
    "agent": {
        "ephemeral_id": "6bbf5dd0-e14b-4006-ac77-ee175a9e81b8",
        "id": "6713ae74-2a36-4e79-bc7b-954d6b48d5bd",
        "name": "docker-fleet-agent",
        "type": "filebeat",
        "version": "8.4.1"
    },
    "citrix_adc": {
        "interface": {
            "disabled": {
                "count": 0
            },
            "link": {
                "down_time": "00:00:11",
                "up_time": "4.06:45:16"
            },
            "mac": {
                "moved": {
                    "count": 0,
                    "rate": 0
                }
            },
            "packets": {
                "inbound": {
                    "dropped": {
                        "count": 2797172,
                        "rate": 32
                    },
                    "dropped_by_hardware": {
                        "count": 0,
                        "rate": 0
                    },
                    "error_free": {
                        "discarded": {
                            "count": 0,
                            "rate": 0
                        }
                    }
                },
                "outbound": {
                    "dropped_by_hardware": {
                        "count": 0,
                        "rate": 0
                    },
                    "error_free": {
                        "discarded": {
                            "count": 0,
                            "rate": 0
                        }
                    }
                },
                "received": {
                    "count": 5396347,
                    "jumbo": {
                        "count": 0,
                        "rate": 0
                    },
                    "multicast": {
                        "count": 278537,
                        "rate": 0
                    },
                    "rate": 38,
                    "tagged": {
                        "count": 0,
                        "rate": 0
                    }
                },
                "transmission": {
                    "dropped": {
                        "count": 0,
                        "rate": 0
                    }
                },
                "transmitted": {
                    "count": 2511171,
                    "jumbo": {
                        "count": 0,
                        "rate": 0
                    },
                    "rate": 5,
                    "tagged": {
                        "count": 0,
                        "rate": 0
                    }
                }
            },
            "received": {
                "bytes": {
                    "rate": 4603,
                    "value": 1103884030
                }
            },
            "stalled": {
                "count": 0
            },
            "state": "UP",
            "transmitted": {
                "bytes": {
                    "rate": 1924,
                    "value": 776571650
                }
            }
        }
    },
    "data_stream": {
        "dataset": "citrix_adc.interface",
        "namespace": "ep",
        "type": "logs"
    },
    "ecs": {
        "version": "8.4.0"
    },
    "elastic_agent": {
        "id": "6713ae74-2a36-4e79-bc7b-954d6b48d5bd",
        "snapshot": false,
        "version": "8.4.1"
    },
    "event": {
        "agent_id_status": "verified",
        "category": [
            "web"
        ],
        "created": "2022-10-07T06:24:46.588Z",
        "dataset": "citrix_adc.interface",
        "ingested": "2022-10-07T06:24:50Z",
        "kind": "event",
        "module": "citrix_adc",
        "original": "{\"curintfstate\":\"UP\",\"curlinkdowntime\":\"00:00:11\",\"curlinkstate\":\"DOWN\",\"curlinkuptime\":\"4.06:45:16\",\"errdroppedrxpkts\":\"2797172\",\"errdroppedrxpktsrate\":32,\"errdroppedtxpkts\":\"0\",\"errdroppedtxpktsrate\":0,\"errifindiscards\":\"0\",\"errifindiscardsrate\":0,\"errlinkhangs\":\"0\",\"errnicmuted\":\"0\",\"errpktrx\":\"0\",\"errpktrxrate\":0,\"errpkttx\":\"0\",\"errpkttxrate\":0,\"id\":\"0/1\",\"interfacealias\":\"\",\"jumbopktsreceived\":\"0\",\"jumbopktsreceivedrate\":0,\"jumbopktstransmitted\":\"0\",\"jumbopktstransmittedrate\":0,\"linkreinits\":\"0\",\"macmovedrate\":0,\"netscalerpktsrate\":6,\"nicerrdisables\":\"0\",\"nicerrifoutdiscards\":\"0\",\"nicerrifoutdiscardsrate\":0,\"nicmulticastpktsrate\":0,\"nicrxstalls\":\"0\",\"nicstsstalls\":\"0\",\"nictotmulticastpkts\":\"278537\",\"nictxstalls\":\"0\",\"rxbytesrate\":4603,\"rxcrcerrors\":\"0\",\"rxcrcerrorsrate\":0,\"rxlacpdu\":\"0\",\"rxlacpdurate\":0,\"rxpktsrate\":38,\"totmacmoved\":\"0\",\"totnetscalerpkts\":\"2493179\",\"totrxbytes\":\"1103884064\",\"totrxpkts\":\"5396347\",\"tottxbytes\":\"776571619\",\"tottxpkts\":\"2511171\",\"trunkpktsreceived\":\"0\",\"trunkpktsreceivedrate\":0,\"trunkpktstransmitted\":\"0\",\"trunkpktstransmittedrate\":0,\"txbytesrate\":1924,\"txlacpdu\":\"0\",\"txlacpdurate\":0,\"txpktsrate\":5}",
        "type": [
            "info"
        ]
    },
    "input": {
        "type": "httpjson"
    },
    "interface": {
        "id": "0/1"
    },
    "tags": [
        "preserve_original_event",
        "citrix_adc-interface",
        "forwarded"
    ]
}
```

**Exported fields**

| Field | Description | Type | Unit | Metric Type |
|---|---|---|---|---|
| @timestamp | Event timestamp. | date |  |  |
| citrix_adc.interface.disabled.count | Number of times the specified interface is disabled by the NetScaler. | float |  | counter |
| citrix_adc.interface.link.down_time | Duration for which the link is DOWN. | keyword |  |  |
| citrix_adc.interface.link.up_time | Duration for which the link is UP. | keyword |  |  |
| citrix_adc.interface.mac.moved.count | Number of MAC moves between ports. | float |  | counter |
| citrix_adc.interface.mac.moved.rate | Rate (/s) counter for totmacmoved. | float |  | gauge |
| citrix_adc.interface.packets.inbound.dropped.count | Number of inbound packets dropped by the specified interface. | float |  | counter |
| citrix_adc.interface.packets.inbound.dropped.rate | Rate (/s) counter for errdroppedrxpkts. | float |  | gauge |
| citrix_adc.interface.packets.inbound.dropped_by_hardware.count | Number of inbound packets dropped by the hardware on a specified interface once the NetScaler appliance starts or the interface statistics are cleared. | float |  | counter |
| citrix_adc.interface.packets.inbound.dropped_by_hardware.rate | Rate (/s) counter for errpktrx. | float |  | gauge |
| citrix_adc.interface.packets.inbound.error_free.discarded.count | Number of error-free inbound packets discarded by the specified interface due to a lack of resources. | float |  | counter |
| citrix_adc.interface.packets.inbound.error_free.discarded.rate | Rate (/s) counter for errifindiscards. | float |  | gauge |
| citrix_adc.interface.packets.outbound.dropped_by_hardware.count | Number of outbound packets dropped by the hardware on a specified interface since the NetScaler appliance was started or the interface statistics were cleared. | float |  | counter |
| citrix_adc.interface.packets.outbound.dropped_by_hardware.rate | Rate (/s) counter for errpkttx. | float |  | gauge |
| citrix_adc.interface.packets.outbound.error_free.discarded.count | Number of error-free outbound packets discarded by the specified interface due to a lack of resources. | float |  | counter |
| citrix_adc.interface.packets.outbound.error_free.discarded.rate | Rate (/s) counter for nicerrifoutdiscards. | float |  | gauge |
| citrix_adc.interface.packets.received.count | Number of packets received by an interface since the NetScaler appliance was started or the interface statistics were cleared. | float |  | counter |
| citrix_adc.interface.packets.received.jumbo.count | Number of Jumbo Packets received on specified interface. | float |  | counter |
| citrix_adc.interface.packets.received.jumbo.rate | Rate (/s) counter for jumbopktsreceived. | float |  | gauge |
| citrix_adc.interface.packets.received.multicast.count | Number of multicast packets received by the specified interface since the NetScaler appliance was started or the interface statistics were cleared. | float |  | counter |
| citrix_adc.interface.packets.received.multicast.rate | Rate (/s) counter for nictotmulticastpkts. | float |  | gauge |
| citrix_adc.interface.packets.received.rate | Rate (/s) counter for totrxpkts. | float |  | gauge |
| citrix_adc.interface.packets.received.tagged.count | Number of Tagged Packets received on specified Trunk interface through Allowed VLan List. | float |  | counter |
| citrix_adc.interface.packets.received.tagged.rate | Rate (/s) counter for trunkpktsreceived. | float |  | gauge |
| citrix_adc.interface.packets.transmission.dropped.count | Number of packets dropped in transmission by the specified interface due to one of the following reasons. (1) VLAN mismatch. (2) Oversized packets. (3) Interface congestion. (4) Loopback packets sent on non loopback interface. | float |  |  |
| citrix_adc.interface.packets.transmission.dropped.rate | Rate (/s) counter for errdroppedtxpkts. | float |  |  |
| citrix_adc.interface.packets.transmitted.count | Number of packets transmitted by an interface since the NetScaler appliance was started or the interface statistics were cleared. | float |  | counter |
| citrix_adc.interface.packets.transmitted.jumbo.count | Number of Jumbo packets transmitted on specified interface by upper layer, with TSO enabled actual trasmission size could be non Jumbo. | float |  | counter |
| citrix_adc.interface.packets.transmitted.jumbo.rate | Rate (/s) counter for jumbopktstransmitted. | float |  | gauge |
| citrix_adc.interface.packets.transmitted.rate | Rate (/s) counter for tottxpkts. | float |  | gauge |
| citrix_adc.interface.packets.transmitted.tagged.count | Number of Tagged Packets transmitted on specified Trunk interface through Allowed VLan List. | float |  | counter |
| citrix_adc.interface.packets.transmitted.tagged.rate | Rate (/s) counter for trunkpktstransmitted. | float |  | gauge |
| citrix_adc.interface.received.bytes.rate | Rate (/s) counter for totrxbytes. | float |  | gauge |
| citrix_adc.interface.received.bytes.value | Number of bytes received by an interface since the NetScaler appliance was started or the interface statistics were cleared. | float | byte | counter |
| citrix_adc.interface.stalled.count | Number of times the interface stalled, when receiving packets, since the NetScaler appliance was started or the interface statistics were cleared. | float |  | counter |
| citrix_adc.interface.state | Current state of the specified interface. | keyword |  |  |
| citrix_adc.interface.transmitted.bytes.rate | Rate (/s) counter for tottxbytes. | float |  | gauge |
| citrix_adc.interface.transmitted.bytes.value | Number of bytes transmitted by an interface since the NetScaler appliance was started or the interface statistics were cleared. | float | byte | counter |
| data_stream.dataset | Data stream dataset. | constant_keyword |  |  |
| data_stream.namespace | Data stream namespace. | constant_keyword |  |  |
| data_stream.type | Data stream type. | constant_keyword |  |  |
| ecs.version | ECS version this event conforms to. `ecs.version` is a required field and must exist in all events. When querying across multiple indices -- which may conform to slightly different ECS versions -- this field lets integrations adjust to the schema version of the events. | keyword |  |  |
| error.message | Error message. | match_only_text |  |  |
| event.category | This is one of four ECS Categorization Fields, and indicates the second level in the ECS category hierarchy. `event.category` represents the "big buckets" of ECS categories. For example, filtering on `event.category:process` yields all events relating to process activity. This field is closely related to `event.type`, which is used as a subcategory. This field is an array. This will allow proper categorization of some events that fall in multiple categories. | keyword |  |  |
| event.dataset | Name of the dataset. If an event source publishes more than one type of log or events (e.g. access log, error log), the dataset is used to specify which one the event comes from. It's recommended but not required to start the dataset name with the module name, followed by a dot, then the dataset name. | keyword |  |  |
| event.ingested | Timestamp when an event arrived in the central data store. This is different from `@timestamp`, which is when the event originally occurred.  It's also different from `event.created`, which is meant to capture the first time an agent saw the event. In normal conditions, assuming no tampering, the timestamps should chronologically look like this: `@timestamp` \< `event.created` \< `event.ingested`. | date |  |  |
| event.kind | This is one of four ECS Categorization Fields, and indicates the highest level in the ECS category hierarchy. `event.kind` gives high-level information about what type of information the event contains, without being specific to the contents of the event. For example, values of this field distinguish alert events from metric events. The value of this field can be used to inform how these kinds of events should be handled. They may warrant different retention, different access control, it may also help understand whether the data coming in at a regular interval or not. | keyword |  |  |
| event.module | Name of the module this data is coming from. If your monitoring agent supports the concept of modules or plugins to process events of a given source (e.g. Apache logs), `event.module` should contain the name of this module. | keyword |  |  |
| event.type | This is one of four ECS Categorization Fields, and indicates the third level in the ECS category hierarchy. `event.type` represents a categorization "sub-bucket" that, when used along with the `event.category` field values, enables filtering events down to a level appropriate for single visualization. This field is an array. This will allow proper categorization of some events that fall in multiple event types. | keyword |  |  |
| input.type | Type of Filebeat input. | keyword |  |  |
| interface.id | Interface ID as reported by an observer (typically SNMP interface ID). | keyword |  |  |
| tags | List of keywords used to tag each event. | keyword |  |  |
