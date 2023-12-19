---
categories: ["SmartCity MXP"]
tags: ["examples"] 
title: "CCIXML Version"
linkTitle: "CCIXML"
date: 2023-12-19
type: docs
weight: 40
description:
---
> NOT SECURED Bordero with NO ULDs, TRASPORT INFORMATIONS AND Bordero ID SPECIFICATION

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
            <AirlinePrefix>055</AirlinePrefix>
            <AWBNumber>47177421</AWBNumber>
            <OriginAirportCityCode>SWK</OriginAirportCityCode>
            <DestinationAirportCityCode>LAX</DestinationAirportCityCode>
            <ShipmentDescriptionCode>T</ShipmentDescriptionCode>
            <NumberOfPieces>1</NumberOfPieces>
            <WeightCode>K</WeightCode>
            <Weight>650</Weight>
            <VolumeDetail>
              <VolumeCode>MC</VolumeCode>
              <VolumeAmount>7.90</VolumeAmount>
            </VolumeDetail>
            <ManifestDescriptionOfGoods>CONSOL</ManifestDescriptionOfGoods>
          </ConsignmentDetail>
        </PART4>
        <PART4>
          <ConsignmentDetail>
            <AirlinePrefix>125</AirlinePrefix>
            <AWBNumber>50768524</AWBNumber>
            <OriginAirportCityCode>SWK</OriginAirportCityCode>
            <DestinationAirportCityCode>BKK</DestinationAirportCityCode>
            <ShipmentDescriptionCode>T</ShipmentDescriptionCode>
            <NumberOfPieces>1</NumberOfPieces>
            <WeightCode>K</WeightCode>
            <Weight>274.5</Weight>
            <VolumeDetail>
              <VolumeCode>MC</VolumeCode>
              <VolumeAmount>1.50</VolumeAmount>
            </VolumeDetail>
            <ManifestDescriptionOfGoods>CONSOL</ManifestDescriptionOfGoods>
          </ConsignmentDetail>
          <OtherCustomsInformation>
            <OCI>
              <CustomsInformationIdentifier>ST</CustomsInformationIdentifier>
              <SupplementaryCustomsInformation>..H..MLE..H..</SupplementaryCustomsInformation>
            </OCI>
            <OCI>
              <CustomsInformationIdentifier>ST</CustomsInformationIdentifier>
              <SupplementaryCustomsInformation>..BDX..1234567..BDX..</SupplementaryCustomsInformation>
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
