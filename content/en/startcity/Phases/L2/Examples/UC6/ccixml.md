---
categories: ["SmartCity MXP"]
tags: ["examples"] 
title: "CCIXML Version"
linkTitle: "CCIXML"
date: 2023-12-19
type: docs
weight: 80
description:
---
> Bordero (SECURED WITH RA INDICATION) WITH TRASPORT INFORMATIONS

### Manifest
```xml
<AirlineManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <VersionTypeNumber>8</VersionTypeNumber>
  <EndOfMessageCode>LAST</EndOfMessageCode>
  <FlightIDAndPointOfLoading>
    <FlightIdentification>
      <CarrierCode>AA</CarrierCode>
      <FlightNumber>0000A</FlightNumber>
      <DepartureDay>07</DepartureDay>
      <DepartureMonth>DEC</DepartureMonth>
    </FlightIdentification>
    <AirportCode>MXP</AirportCode>
  </FlightIDAndPointOfLoading>
  <DestinationHeader>
    <PART3>
      <PointOfUnloading>
        <AirportCode>MXP</AirportCode>
      </PointOfUnloading>
      <BulkLoadedCargo>
        <PART4>
          <ConsignmentDetail>
            <AirlinePrefix>074</AirlinePrefix>
            <AWBNumber>51677194</AWBNumber>
            <OriginAirportCityCode>VCE</OriginAirportCityCode>
            <DestinationAirportCityCode>PVG</DestinationAirportCityCode>
            <ShipmentDescriptionCode>T</ShipmentDescriptionCode>
            <NumberOfPieces>4</NumberOfPieces>
            <WeightCode>K</WeightCode>
            <Weight>1.6</Weight>
            <VolumeDetail>
              <VolumeCode>MC</VolumeCode>
              <VolumeAmount>0.0</VolumeAmount>
            </VolumeDetail>
            <ManifestDescriptionOfGoods>CONSOL SHIPMENT</ManifestDescriptionOfGoods>
          </ConsignmentDetail>
        </PART4>
        <PART4>
          <ConsignmentDetail>
            <AirlinePrefix>020</AirlinePrefix>
            <AWBNumber>95524284</AWBNumber>
            <OriginAirportCityCode>VCE</OriginAirportCityCode>
            <DestinationAirportCityCode>PVG</DestinationAirportCityCode>
            <ShipmentDescriptionCode>T</ShipmentDescriptionCode>
            <NumberOfPieces>4</NumberOfPieces>
            <WeightCode>K</WeightCode>
            <Weight>141</Weight>
            <VolumeDetail>
              <VolumeCode>MC</VolumeCode>
              <VolumeAmount>1.5</VolumeAmount>
            </VolumeDetail>
            <ManifestDescriptionOfGoods>OPTICAL ARTICLE</ManifestDescriptionOfGoods>
          </ConsignmentDetail>
          <OtherCustomsInformation>
            <OCI>
              <CustomsInformationIdentifier>ST</CustomsInformationIdentifier>
              <SupplementaryCustomsInformation>..S..1..S..</SupplementaryCustomsInformation>
            </OCI>
            <OCI>
              <ISOCountryCode>IT</ISOCountryCode>
              <InformationIdentifier>ISS</InformationIdentifier>
              <CustomsInformationIdentifier>RA</CustomsInformationIdentifier>
              <SupplementaryCustomsInformation>00125-01</SupplementaryCustomsInformation>
            </OCI>
            <OCI>
              <CustomsInformationIdentifier>ST</CustomsInformationIdentifier>
              <SupplementaryCustomsInformation>..H..MLE..H..</SupplementaryCustomsInformation>
            </OCI>
            <OCI>
              <CustomsInformationIdentifier>ST</CustomsInformationIdentifier>
              <SupplementaryCustomsInformation>..AG..CSF..AG..</SupplementaryCustomsInformation>
            </OCI>
            <OCI>
              <CustomsInformationIdentifier>ST</CustomsInformationIdentifier>
              <SupplementaryCustomsInformation>..DN..JOHN DOE..DN..</SupplementaryCustomsInformation>
            </OCI>
            <OCI>
              <CustomsInformationIdentifier>ST</CustomsInformationIdentifier>
              <SupplementaryCustomsInformation>..DT..DRIVE LIC..DT..</SupplementaryCustomsInformation>
            </OCI>
            <OCI>
              <CustomsInformationIdentifier>ST</CustomsInformationIdentifier>
              <SupplementaryCustomsInformation>..DA..LIC.AUTH...DA..</SupplementaryCustomsInformation>
            </OCI>
            <OCI>
              <CustomsInformationIdentifier>ST</CustomsInformationIdentifier>
              <SupplementaryCustomsInformation>..DI..ABC458879..DI..</SupplementaryCustomsInformation>
            </OCI>
            <OCI>
              <CustomsInformationIdentifier>ST</CustomsInformationIdentifier>
              <SupplementaryCustomsInformation>..PN..ZF 676 TG..PN..</SupplementaryCustomsInformation>
            </OCI>
            <OCI>
              <CustomsInformationIdentifier>ST</CustomsInformationIdentifier>
              <SupplementaryCustomsInformation>..SN..SEAL1..SN..</SupplementaryCustomsInformation>
            </OCI>
            <OCI>
              <CustomsInformationIdentifier>ST</CustomsInformationIdentifier>
              <SupplementaryCustomsInformation>..CN..JOHN DOE LTD..CN..</SupplementaryCustomsInformation>
            </OCI>
            <OCI>
              <CustomsInformationIdentifier>ST</CustomsInformationIdentifier>
              <SupplementaryCustomsInformation>..TN..JOHN DOE TRANSPORT..TN..</SupplementaryCustomsInformation>
            </OCI>
          </OtherCustomsInformation>
        </PART4>
      </BulkLoadedCargo>
    </PART3>
  </DestinationHeader>
</AirlineManifest>
```
