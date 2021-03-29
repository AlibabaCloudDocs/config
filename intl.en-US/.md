# Appendix: ACS::OOS::Inventory

ACS::OOS::Inventory indicates the configuration list of an OOS instance. The configuration list includes various configuration data. The configuration data includes the environment information of the instance, settings for applications, settings for system files, network settings, registry information, information for system updates, and settings for updates.

Cloud Config traces and records the change snapshots of configuration lists in a continuous manner. The default retention period for these change snapshots is 10 years. You can view a configuration snapshot for a configuration list at a historical point in time. You can also call an API operation to obtain the required configuration data. ACS::OOS::Inventory includes multiple data structures. For more information, see the following code.

```
[
  {
    "TypeName": "ACS:InstanceInformation", //The information of the required instance.
    "Version": "1.0",
    "Attributes": [
      {
        "DataType": "STRING",
        "Name": "AgentType" //The agent type.
      },
      {
        "DataType": "STRING",
        "Name": "AgentVersion" //The agent version.
      },
      {
        "DataType": "STRING",
        "Name": "ComputerName" //The host name.
      },
      {
        "DataType": "STRING",
        "Name": "RamRole" //The RAM role.
      },
      {
        "DataType": "STRING",
        "Name": "InstanceId" //The instance ID.
      },
      {
        "DataType": "STRING",
        "Name": "IpAddress" //The private IP address.
      },
      {
        "DataType": "STRING",
        "Name": "PlatformName" //The platform name.
      },
      {
        "DataType": "STRING",
        "Name": "PlatformType"  //The platform type.
      },
      {
        "DataType": "STRING",
        "Name": "PlatformVersion" //The platform version.
      },
      {
        "DataType": "STRING",
        "Name": "ResourceType" //The resource type.
      },
      {
        "DataType": "STRING",
        "Name": "Status" //The instance status.
      }
    ]
  },
  {
    "TypeName": "ACS:Application", //The information of an application.
    "Version": "1.0",
    "Attributes": [
      {
        "DataType": "STRING",
        "Name": "Name"  //The application name.
      },
      {
        "DataType": "STRING",
        "Name": "ApplicationType" //The application type.
      },
      {
        "DataType": "STRING",
        "Name": "Publisher" //The operator who publishes the application.
      },
      {
        "DataType": "STRING",
        "Name": "Version" //The application version.
      },
      {
        "DataType": "STRING",
        "Name": "InstalledTime" //The time when the application is installed.
      },
      {
        "DataType": "STRING",
        "Name": "Architecture" //The architecture.
      },
      {
        "DataType": "STRING",
        "Name": "URL" //The download URL of the application.
      },
      {
        "DataType": "STRING",
        "Name": "Summary" //The abstract of the application.
      },
      {
        "DataType": "STRING",
        "Name": "PackageId" //The ID of the application package.
      },
      {
        "DataType": "STRING",
        "Name": "Release" //The release version.
      }
    ]
  },
  {
    "TypeName": "ACS:File", //The information of a file list.
    "Version": "1.0",
    "Attributes": [
      {
        "DataType": "STRING",
        "Name": "Name" //The name of a file.
      },
      {
        "DataType": "STRING",
        "Name": "Size" //The size of the file.
      },
      {
        "DataType": "STRING",
        "Name": "Description" //The description of the file.
      },
      {
        "DataType": "STRING",
        "Name": "FileVersion"
      },
      {
        "DataType": "STRING",
        "Name": "InstalledDate"
      },
      {
        "DataType": "STRING",
        "Name": "ModificationTime" //The time when the file is changed.
      },
      {
        "DataType": "STRING",
        "Name": "LastAccessTime" //The last visit time of the file.
      },
      {
        "DataType": "STRING",
        "Name": "ProductName"
      },
      {
        "DataType": "STRING",
        "Name": "InstalledDir" //The directory where the file resides.
      },
      {
        "DataType": "STRING",
        "Name": "ProductLanguage"
      },
      {
        "DataType": "STRING",
        "Name": "CompanyName"
      },
      {
        "DataType": "STRING",
        "Name": "ProductVersion"
      }
    ]
  },
  {
    "TypeName": "ACS:Network", //The network status.
    "Version": "1.0",
    "Attributes": [
      {
        "DataType": "STRING",
        "Name": "Name" //The NIC card name.
      },
      {
        "DataType": "STRING",
        "Name": "SubnetMask"
      },
      {
        "DataType": "STRING",
        "Name": "Gateway"
      },
      {
        "DataType": "STRING",
        "Name": "DHCPServer" //The IP address of the DHCP server.
      },
      {
        "DataType": "STRING",
        "Name": "DNSServer" //The IP address of the DNS server.
      },
      {
        "DataType": "STRING",
        "Name": "MacAddress"
      },
      {
        "DataType": "STRING",
        "Name": "IPV4" //The IPv4 address.
      },
      {
        "DataType": "STRING",
        "Name": "IPV6" //The IPv6 address.
      }
    ]
  },
  {
    "TypeName": "ACS:WindowsRole", //The Windows role.
    "Version": "1.0",
    "Attributes": [
      {
        "DataType": "STRING",
        "Name": "Name" //The role name.
      },
      {
        "DataType": "STRING",
        "Name": "DisplayName" //The feature name.
      },
      {
        "DataType": "STRING",
        "Name": "Description" //The description.
      },
      {
        "DataType": "STRING",
        "Name": "Installed"
      },
      {
        "DataType": "STRING",
        "Name": "InstalledState" //The status.
      },
      {
        "DataType": "STRING",
        "Name": "FeatureType"  //The feature type. Valid value: role.
      },
      {
        "DataType": "STRING",
        "Name": "Path"
      },
      {
        "DataType": "STRING",
        "Name": "SubFeatures"
      },
      {
        "DataType": "STRING",
        "Name": "ServerComponentDescriptor"
      },
      {
        "DataType": "STRING",
        "Name": "DependsOn"
      },
      {
        "DataType": "STRING",
        "Name": "Parent"
      }
    ]
  },
  {
    "TypeName": "ACS:Service", //A service that runs on the instance.
    "Version": "1.0",
    "Attributes": [
      {
        "DataType": "STRING",
        "Name": "Name" //The service name.
      },
      {
        "DataType": "STRING",
        "Name": "DisplayName" //The feature name.
      },
      {
        "DataType": "STRING",
        "Name": "Status" //The status of the service.
      },
      {
        "DataType": "STRING",
        "Name": "DependentServices"
      },
      {
        "DataType": "STRING",
        "Name": "ServicesDependedOn"
      },
      {
        "DataType": "STRING",
        "Name": "ServiceType" //The type of the service.
      },
      {
        "DataType": "STRING",
        "Name": "StartType" //The startup method of the service.
      }
    ]
  },
  {
    "TypeName": "ACS:WindowsRegistry", //The information of a Windows registry key.
    "Version": "1.0",
    "Attributes": [
      {
        "DataType": "STRING",
        "Name": "ValueName" //The name of the registry key.
      },
      {
        "DataType": "STRING",
        "Name": "ValueType" //The type of the registry key.
      },
      {
        "DataType": "STRING",
        "Name": "KeyPath" //The path of the registry key.
      },
      {
        "DataType": "STRING",
        "Name": "Value" //The value of the registry key.
      }
    ]
  },
  {
    "TypeName": "ACS:WindowsUpdate", //The information of a Windows update record.
    "Version": "1.0",
    "Attributes": [
      {
        "DataType": "STRING",
        "Name": "HotFixId" //The update ID.
      },
      {
        "DataType": "STRING",
        "Name": "Description" //The description.
      },
      {
        "DataType": "STRING",
        "Name": "InstalledTime" //The time when the update is installed.
      },
      {
        "DataType": "STRING",
        "Name": "InstalledBy" //The operator who creates the update.
      }
    ]
  }
]
```

