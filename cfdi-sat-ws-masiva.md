```php
// Crear la consulta detallada $query = QueryParameters::create() ->withPeriod(DateTimePeriod::createFromValues('2024-01-01 00:00:00', '2024-01-31 23:59:59')) // Define el periodo ->withDownloadType(DownloadType::received()) // Tipo de descarga: recibidos ->withRequestType(RequestType::xml()) // Solicitar archivos XML ->withDocumentType(DocumentType::ingreso()) // Filtrar por documentos de tipo ingreso ->withComplement(ComplementoCfdi::leyendasFiscales10()) // Filtrar por complemento de leyendas fiscales ->withDocumentStatus(DocumentStatus::active()) // Filtrar por documentos vigentes ->withRfcOnBehalf(RfcOnBehalf::create('XXX01010199A')) // Filtrar por RFC a cuenta de terceros ->withRfcMatch(RfcMatch::create('MAG041126GT8')) // Filtrar por RFC contraparte (emitidos por este RFC) ->withUuid(Uuid::create('96623061-61fe-49de-b298-c7156476aa8b')) // Filtrar por UUID específico ;
```