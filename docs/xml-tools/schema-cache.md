---
title: Schema Cache des XML-Editors
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40781a5249d9b69df5f41f863f3d36ac6a119645
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592489"
---
# <a name="schema-cache"></a>Schemacache

Der XML-Editor stellt einen Schema Cache bereit, der sich im Verzeichnis *%VSInstallDir%\Xml\Schemas* befindet. Der Schema Cache ist global für alle Benutzer auf dem Computer und umfasst Standard-XML-Schemas, die für IntelliSense und die Validierung von XML-Dokumenten verwendet werden.

Der XML-Editor kann auch Schemas suchen, die sich in der Projekt Mappe befinden, Schemas, die im Feld **Schemas** des Dokument **Eigenschaften** Fensters angegeben sind, und Schemas, die durch die Attribute `xsi:schemaLocation` und `xsi:noNamespaceSchemaLocation` identifiziert werden.

In der folgenden Tabelle werden die Schemas beschrieben, die mit dem XML-Editor installiert werden.

| Dateiname | Beschreibung |
|-| - |
| *Catalog. xsd* | Schema für Schemakatalogdateien des XML-Editors. Weitere Informationen zu den Schemakatalogen finden Sie weiter unten. |
| *DotNetConfig.xsd* | Schema für Web. config-Dateien, `http://schemas.microsoft.com/.NETConfiguration/v2.0`. |
| *msbuild.xsd* | Schema für die MSBuild-Dateien zum Erstellen von Dateien, `http://schemas.microsoft.com/developer/msbuild/2003`. |
| *msdata.xsd* | Schema für XSD-Anmerkungen, die von der <xref:System.Data.DataSet>-Klasse hinzugefügt werden, "urn:schemas-microsoft-com:xml-msdata". |
| *msxsl.xsd* | Schema für Microsoft XSLT-Skriptblockerweiterungen, urn:schemas-microsoft-com:xslt. |
| *SnippetFormat.xsd* | Schema für die XML-Dateien von Codeausschnitten. Beispiele finden Sie unter *% VSInstallDir% \VC#\erweiterungen*. |
| *SOAP 1.1. xsd* | Schema für SOAP (Simple Object Access Protocol) 1,1, `http://schemas.xmlsoap.org/soap/envelope/`. |
| *SOAP 1.2. xsd* | Schema für Simple Object Access Protocol 1.2. |
| *SiteMapSchema.xsd* | Schema für die ASP.net-Sitemap-XML-Datei, `http://schemas.microsoft.com/AspNet/SiteMap-File-1.0`. |
| *wsdl.xsd* | Schema für die Webdienst-Beschreibungssprache, `http://schemas.xmlsoap.org/wsdl/`. |
| *xenc.xsd* | Schema für die XML-Verschlüsselung, `http://www.w3.org/2000/09/xmldsig#`. |
| *xhtml.xsd* | Schema für XHTML-`http://www.w3.org/1999/xhtml`. |
| *xlink.xsd* | Schema für XLink 1.0, `http://www.w3.org/1999/xlink`. |
| *xml.xsd* | Schema, das XML: Space-und XML: lang-Attribute beschreibt, `http://www.w3.org/XML/1998/namespace`. |
| *xmlsig.xsd* | Schema für digitale XML-Signaturen, `http://www.w3.org/2000/09/xmldsig#`. |
| *xsdschema.xsd* | Schema, das XSD selbst beschreibt, `http://www.w3.org/2001/XMLSchema`. |
| *xslt.xsd* | Schema für XML-Transformationen, `http://www.w3.org/1999/XSL/Transform`. |

## <a name="update-schemas-in-the-cache"></a>Aktualisieren von Schemas im Cache

Der Editor lädt das Verzeichnis des Schemacache beim Laden des XML-Editorpakets und überwacht während der Ausführung alle Änderungen. Wenn ein Schema hinzugefügt wurde, wird es automatisch in einen Index bekannter Schemata im Speicher geladen. Wenn ein Schema entfernt wurde, wird es automatisch vom Index im Speicher entfernt. Wenn ein Schema aktualisiert wurde, wird es automatisch im speicherinternen Cache dieses Schemas für ungültig erklärt.

> [!NOTE]
> Da das Verzeichnis des Schemacaches für Ihren Computer global ist, sollten Sie hier nur standardmäßige Schemas hinzufügen, die für alle auf dem Computer erstellten Visual Studio-Projekte nützlich sind.

Der XML-Editor unterstützt eine beliebige Anzahl von Schemakatalogdateien im Verzeichnis des Schemacaches. Schemakataloge können auf andere Speicherorte von Schemata zeigen, die dem Editor immer bekannt sein sollen. Die *catalog. xsd* -Datei definiert das Format für die Katalog Datei und ist im Schema Cache Verzeichnis enthalten. Die *catalog. XML* -Datei ist der Standardkatalog und enthält Links zu anderen Schemas in *% VSInstallDir%* . Im folgenden finden Sie eine Stichprobe der Datei *catalog. XML* :

```xml
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%VSInstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

Das `href`-Attribut kann jede/r Dateipfad oder HTTP-URL sein, der/die auf das Schema zeigt. Der Dateipfad kann relativ zum Katalogdokument sein. Die folgenden Variablen, die durch%% getrennt sind, werden vom Editor erkannt und im Pfad erweitert:

- VSInstallDir

- System

- ProgramFiles

- Programs

- CommonProgramFiles

- ApplicationData

- CommonApplicationData

- LCID

Das Katalogdokument kann ein `Catalog`-Element enthalten, das auf andere Kataloge zeigt. Mithilfe des `Catalog`-Elements können Sie auf einen für Ihr Team oder Ihr Unternehmen freigegebenen zentralen Katalog oder auf einen Onlinekatalog zeigen, den Sie gemeinsam mit Ihren Geschäftspartnern nutzen. Das `href`-Attribut ist der Dateipfad oder die HTTP-URL für die anderen Kataloge. Es folgt ein Beispiel für das `Catalog`-Element:

```xml
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

Der Katalog kann auch steuern, wie die Schemata den XML-Dokumenten mithilfe des speziellen `Association`-Elements zugeordnet werden. Dieses Element ordnet Schemas zu, die über keinen Ziel Namespace mit einer bestimmten Dateierweiterung verfügen. Dies kann hilfreich sein, da der XML-Editor keine automatische Zuordnung von Schemas durchführt, die kein `targetNamespace` Attribut aufweisen. Im folgenden Beispiel ordnet das `Association`-Element allen Dateien das dotNetConfig-Schema zu, die die config-Dateierweiterung aufweisen:

```xml
<Association extension="config" schema="%VSInstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>Lokalisierte Schemas

In vielen Fällen enthält die *catalog. XML* -Datei keine Einträge für lokalisierte Schemas. Sie können der Datei *catalog. XML* zusätzliche Einträge hinzufügen, die auf das lokalisierte Schema Verzeichnis verweisen.

Im folgenden Beispiel wurde ein neues `Schema`-Element erstellt, das mithilfe der %LCID%-Variable auf das lokalisierte Schema verweist.

```xml
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="change-the-location-of-the-schema-cache"></a>Ändern des Speicher Orts für den Schema Cache

Sie können den Speicherort für den Schema Cache mithilfe der Seite **verschiedene** Optionen anpassen. Wenn Sie über ein Verzeichnis der bevorzugten Schemata verfügen, kann der Editor so konfiguriert werden, dass er stattdessen diese Schemata verwendet.

> [!NOTE]
> Von dieser Änderung ist nur der aktuelle Benutzer von Visual Studio betroffen.

### <a name="to-change-the-schema-cache-location"></a>So ändern Sie den Speicherort für den Schemacache

1. Wählen Sie **im Menü** Extras die **Option Optionen**aus.

2. Erweitern Sie **Text-Editor**, erweitern Sie **XML**, und klicken Sie dann auf **Verschiedenes**.

3. Klicken Sie im Feld **Schemas** auf die Schaltfläche **Durchsuchen** .

4. Wählen Sie den Ordner für den Schema Cache aus, und klicken Sie auf **OK**.

### <a name="to-add-another-directory-of-common-schemas"></a>So fügen Sie ein anderes Verzeichnis für häufig verwendete Schemata hinzu

1. Bearbeiten Sie die Datei *catalog. XML* im Schema Cache Verzeichnis des XML-Editors.

2. Fügen Sie ein neues `<Catalog href="..."/>`-Element hinzu, das auf das Verzeichnis der zusätzlichen Schemata zeigt.

3. Speichern Sie die Änderungen.

   Der Katalog wird automatisch neu geladen.

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)
