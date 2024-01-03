---
categories: ["SmartCity MXP"]
tags: ["examples"] 
title: "CCIXML Version"
linkTitle: "CCIXML"
date: 2023-12-12
type: docs
weight: 40
description:
---
> AWB AND HAWB TRANSMISSION MESSAGE INCLUDING A CUSTOMS DECLARATION AND THE RELATED SECURITY CHECK


### MAWB
```xml
<?xml version="1.0" encoding="utf-8"?>
<Master xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <VersionTypeNumber>16</VersionTypeNumber>
  <AWBConsignmentDetail>
    <AirlinePrefix>888</AirlinePrefix>
    <AWBNumber>14467110</AWBNumber>
    <OriginAirportCityCode>MXP</OriginAirportCityCode>
    <DestinationAirportCityCode>NRT</DestinationAirportCityCode>
    <ShipmentDescriptionCode>T</ShipmentDescriptionCode>
    <NumberOfPieces>10</NumberOfPieces>
    <WeightCode>K</WeightCode>
    <Weight>89.10</Weight>
  </AWBConsignmentDetail>
  <FlightBookings>
    <FLT>
      <CarrierCode>KZ</CarrierCode>
      <FlightNumber>089</FlightNumber>
      <Day>07</Day>
    </FLT>
  </FlightBookings>
  <Routing>
    <DestinationCarrierAirportCityCode>MXP</DestinationCarrierAirportCityCode>
    <DestinationCarrierCode>KZ</DestinationCarrierCode>
    <OnwardDestinationCarrierList>
      <ODC>
        <OnwardDestinationCarrierAirportCityCode>NRT</OnwardDestinationCarrierAirportCityCode>
        <OnwardDestinationCarrierCode>KZ</OnwardDestinationCarrierCode>
      </ODC>
    </OnwardDestinationCarrierList>
  </Routing>
  <Shipper>
    <Name>XXX SPA</Name>
    <StreetAddress>VIA ROMA 144</StreetAddress>
    <Place>ROMA</Place>
    <StateProvince>ITALIA</StateProvince>
    <IsoCountryCode>IT</IsoCountryCode>
  </Shipper>
  <Consignee>
    <Name>XXXXXXXX CO. LTD.</Name>
    <StreetAddress>XXXXXXXXXXXXXXXXX</StreetAddress>
    <Place>XXXXXXXXXXXXXXXX</Place>
    <IsoCountryCode>XX</IsoCountryCode>
    <PostCode>40667</PostCode>
    <ContactDetails>
      <ContactDetailElement>
        <ContactIdentifier>TE</ContactIdentifier>
        <ContactNumber>0000000000</ContactNumber>
      </ContactDetailElement>
    </ContactDetails>
  </Consignee>
  <Agent>
    <IATACargoAgentNumericCode>0000000</IATACargoAgentNumericCode>
    <IATACargoAgentCASSAddress>0015</IATACargoAgentCASSAddress>
    <Name>XXXXXXXXXXXXXXXXXX</Name>
    <Place>XXXXXXXXXXX</Place>
  </Agent>
  <SpecialServiceRequest>ONE POUCH ATTACHED TO AIRWAY BILL</SpecialServiceRequest>
  <ChargeDeclarations>
    <ISOCurrencyCode>EUR</ISOCurrencyCode>
    <ChargeCode>PP</ChargeCode>
    <PrepaidCollectWeightValuation>P</PrepaidCollectWeightValuation>
    <PrepaidCollectOtherCharges>P</PrepaidCollectOtherCharges>
    <DeclaredValueForCarriage>NVD</DeclaredValueForCarriage>
    <DeclaredValueForCustoms>NCV</DeclaredValueForCustoms>
    <AmountForInsurance>XXX</AmountForInsurance>
  </ChargeDeclarations>
  <RateDescription>
    <RTD>
      <AWBRateLineNumber>1</AWBRateLineNumber>
      <NumberOfPiecesOrRateCombinationPoint>1</NumberOfPiecesOrRateCombinationPoint>
      <GrossWeightCode>K</GrossWeightCode>
      <GrossWeight>2</GrossWeight>
      <RateClassCode>M</RateClassCode>
      <ChargeableWeight>5.5</ChargeableWeight>
      <TotalDetailsChargeOrDiscountAmount>250.0</TotalDetailsChargeOrDiscountAmount>
      <GoodsDescriptionNatureAndQuantityOfGoods>AIRCRAFT PARTS A</GoodsDescriptionNatureAndQuantityOfGoods>
    </RTD>
    <RTD>
      <AWBRateLineNumber>2</AWBRateLineNumber>
      <GoodsDescriptionNatureAndQuantityOfGoods>OG AOG AO</GoodsDescriptionNatureAndQuantityOfGoods>
    </RTD>
    <RTD>
      <AWBRateLineNumber>3</AWBRateLineNumber>
      <GoodsDescriptionNatureAndQuantityOfGoods>G XPS</GoodsDescriptionNatureAndQuantityOfGoods>
    </RTD>
    <RTD>
      <AWBRateLineNumber>4</AWBRateLineNumber>
      <GoodsDescriptionNatureAndQuantityOfGoods>XPS XPS NOT R</GoodsDescriptionNatureAndQuantityOfGoods>
    </RTD>
    <RTD>
      <AWBRateLineNumber>5</AWBRateLineNumber>
      <GoodsDescriptionNatureAndQuantityOfGoods>ESTRICTED</GoodsDescriptionNatureAndQuantityOfGoods>
    </RTD>
    <RTD>
      <AWBRateLineNumber>6</AWBRateLineNumber>
      <Volume>
        <VolumeCode>MC</VolumeCode>
        <VolumeAmount>0.03</VolumeAmount>
      </Volume>
    </RTD>
    <RTD>
      <AWBRateLineNumber>7</AWBRateLineNumber>
      <Dimensions>
        <MeasurementUnitCode>NDA</MeasurementUnitCode>
        <NumberOfPieces xsi:nil="true" />
      </Dimensions>
    </RTD>
  </RateDescription>
  <OtherCharges>
    <OTH>
      <OtherChargesIndicator>P</OtherChargesIndicator>
      <OtherCharges>
        <OTS>
          <OtherChargeCode>MC</OtherChargeCode>
          <EntitlementCode>A</EntitlementCode>
          <ChargeAmount>12.00</ChargeAmount>
        </OTS>
        <OTS>
          <OtherChargeCode>MC</OtherChargeCode>
          <EntitlementCode>C</EntitlementCode>
          <ChargeAmount>5.97</ChargeAmount>
        </OTS>
        <OTS>
          <OtherChargeCode>MY</OtherChargeCode>
          <EntitlementCode>C</EntitlementCode>
          <ChargeAmount>623.70</ChargeAmount>
        </OTS>
      </OtherCharges>
    </OTH>
    <OTH>
      <OtherChargesIndicator>P</OtherChargesIndicator>
      <OtherCharges>
        <OTS>
          <OtherChargeCode>SC</OtherChargeCode>
          <EntitlementCode>C</EntitlementCode>
          <ChargeAmount>13.36</ChargeAmount>
        </OTS>
      </OtherCharges>
    </OTH>
  </OtherCharges>
  <PrepaidChargeSummary>
    <TotalWeightChargeAmount>1052.40</TotalWeightChargeAmount>
    <TotalOtherChargesDueAgentAmount>12.00</TotalOtherChargesDueAgentAmount>
    <TotalOtherChargesDueCarrierAmount>643.03</TotalOtherChargesDueCarrierAmount>
    <ChargeSummaryTotalAmount>1707.43</ChargeSummaryTotalAmount>
  </PrepaidChargeSummary>
  <ShippersCertificationsSignature>XXX SPA</ShippersCertificationsSignature>
  <CarriersExecution>
    <IssueDate>05MAR15</IssueDate>
    <PlaceOrAirportCityCode>BRT</PlaceOrAirportCityCode>
    <AuthorizationSignature>NIPPON CARGO AIRLINE</AuthorizationSignature>
  </CarriersExecution>
  <SenderReference>
    <SenderParticipantIdentification>
      <ParticipantIdentifier>AGT</ParticipantIdentifier>
      <ParticipantCode>XXXSRL</ParticipantCode>
      <ParticipantAirportCityCode>NRT</ParticipantAirportCityCode>
    </SenderParticipantIdentification>
  </SenderReference>
  <CustomsOriginCode>X</CustomsOriginCode>
  <SpecialHandlingRequirements>
    <SHR>
      <SpecialHandlingCode>SPX</SpecialHandlingCode>
    </SHR>
  </SpecialHandlingRequirements>
  <OtherCustomsInformation>
    <OCI>
      <ISOCountryCode>IT</ISOCountryCode>
      <InformationIdentifier>ISS</InformationIdentifier>
      <CustomsInformationIdentifier>RA</CustomsInformationIdentifier>
      <SupplementaryCustomsInformation>00000-01</SupplementaryCustomsInformation>
    </OCI>
    <OCI>
      <CustomsInformationIdentifier>ED</CustomsInformationIdentifier>
      <SupplementaryCustomsInformation>0717</SupplementaryCustomsInformation>
    </OCI>
    <OCI>
      <CustomsInformationIdentifier>SM</CustomsInformationIdentifier>
      <SupplementaryCustomsInformation>XRY</SupplementaryCustomsInformation>
    </OCI>
  </OtherCustomsInformation>
</Master>
```

### HAWB

```xml
<?xml version="1.0" encoding="utf-8"?>
<House xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <VersionTypeNumber>4</VersionTypeNumber>
  <MasterAWBConsignmentDetail>
    <AirlinePrefix>888</AirlinePrefix>
    <AWBNumber>14467110</AWBNumber>
    <OriginAirportCityCode>MXP</OriginAirportCityCode>
    <DestinationAirportCityCode>NRT</DestinationAirportCityCode>
    <ShipmentDescriptionCode>T</ShipmentDescriptionCode>
    <NumberOfPieces>10</NumberOfPieces>
    <WeightCode>K</WeightCode>
    <Weight>89.10</Weight>
  </MasterAWBConsignmentDetail>
  <CheckList>
    <HouseWaybills>
      <HouseWaybillSummaryDetails>
        <HBS>
          <HWBSerialNumber>ABT172320633</HWBSerialNumber>
          <DepartureAirportCityCode>MXP</DepartureAirportCityCode>
          <DestinationAirportCityCode>NRT</DestinationAirportCityCode>
          <NumberOfPieces>1</NumberOfPieces>
          <WeightCode>K</WeightCode>
          <Weight>4</Weight>
          <SLAC />
          <ManifestDescriptionOfGoods>BAGS</ManifestDescriptionOfGoods>
          <SpecialHandlingRequirements>
            <SHR>
              <SpecialHandlingCode>SPX</SpecialHandlingCode>
            </SHR>
          </SpecialHandlingRequirements>
        </HBS>
      </HouseWaybillSummaryDetails>
      <HarmonisedTariffScheduleInformation />
      <OtherCustomsInformation>
        <OCI>
          <ISOCountryCode>IT</ISOCountryCode>
          <InformationIdentifier>EXP</InformationIdentifier>
          <CustomsInformationIdentifier>M</CustomsInformationIdentifier>
          <SupplementaryCustomsInformation>15ITQ1V1T0253914E0</SupplementaryCustomsInformation>
        </OCI>
        <OCI>
          <InformationIdentifier>COR</InformationIdentifier>
          <SupplementaryCustomsInformation>X</SupplementaryCustomsInformation>
        </OCI>
      </OtherCustomsInformation>
    </HouseWaybills>
  </CheckList>
  <ShipperNameandAddress>
    <Name>XXX SRL</Name>
    <StreetAddress>VIA EMILIA 6</StreetAddress>
    <Place>ROMA</Place>
    <StateProvince>ITALIA</StateProvince>
    <IsoCountryCode>IT</IsoCountryCode>
  </ShipperNameandAddress>
  <ConsigneeNameandAddress>
    <Name>XXX COMMERCE AND TRADING</Name>
    <StreetAddress>ROOM 813 NO.885 REN MIN ROAD</StreetAddress>
    <Place>SHANGHAI</Place>
    <StateProvince>CHINA</StateProvince>
    <IsoCountryCode>CN</IsoCountryCode>
  </ConsigneeNameandAddress>
</House>
```
