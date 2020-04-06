---
title: Persistente Daten in der MSBuild-Projektdatei | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e83526007f676ae94ddce57936b627bcb4308c2a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706693"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Beibehalten von Daten in der MSBuild-Projektdatei
Ein Projektuntertyp muss möglicherweise subtypspezifische Daten zur späteren Verwendung in der Projektdatei beibehalten. Ein Projektuntertyp verwendet die Projektdateipersistenz, um die folgenden Anforderungen zu erfüllen:

1. Persistenzdaten, die im Rahmen der Projekterstellung verwendet werden. (Weitere Informationen zum Microsoft Build-Modul finden Sie unter [MSBuild](../../msbuild/msbuild.md).) Buildbezogene Informationen können entweder:

    1. Konfigurationsunabhängige Daten. Das heißt, Daten, die in MSBuild-Elementen mit leeren oder fehlenden Bedingungen gespeichert sind.

    2. Konfigurationsabhängige Daten. Das heißt, Daten, die in MSBuild-Elementen gespeichert sind, die für eine bestimmte Projektkonfiguration konditioniert sind. Beispiel:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Persistenzdaten, die für den Build nicht relevant sind. Diese Daten können in Freiform-XML ausgedrückt werden, das nicht anhand eines XML-Schemas überprüft wird.

    1. Konfigurationsunabhängige Daten.

    2. Konfigurationsabhängige Daten.

## <a name="persisting-build-related-information"></a>Persistente Build-bezogene Informationen
 Die Persistenz von Daten, die zum Erstellen eines Projekts nützlich sind, wird über MSBuild verarbeitet. Das MSBuild-System verwaltet eine Mastertabelle mit buildbezogenen Informationen. Projektuntertypen sind für den Zugriff auf diese Daten verantwortlich, um Eigenschaftswerte abzusuchen und festzulegen. Projektuntertypen können auch die buildbezogene Datentabelle erweitern, indem zusätzliche Eigenschaften hinzugefügt werden, die beibehalten werden sollen, und Eigenschaften entfernen, damit sie nicht beibehalten werden.

 Zum Ändern der MSBuild-Daten ist ein Projektuntertyp für das Abrufen des <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>MSBuild-Eigenschaftsobjekts aus dem Basisprojektsystem über verantwortlich. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>ist eine Schnittstelle, die im Kernprojektsystem implementiert ist und `QueryInterface`die Projektuntertypabfragen für sie durch Ausführen von .

 Im folgenden Verfahren werden die Schritte <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>zum Entfernen einer Eigenschaft mithilfe von beschrieben.

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>So entfernen Sie eine Eigenschaft aus einer MSBuild-Projektdatei

1. Aufruf `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> des Projektuntertyps.

2. Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> `pszPropName` Sie mit Satz auf die Eigenschaft auf, die Sie entfernen möchten.

### <a name="persisting-non-build-related-information"></a>Persistente nicht buildbezogene Informationen
 Die Persistenz von Daten in Projektdateien, die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>nicht erstellt werden sollen, wird über verarbeitet.

 Sie können <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> für `project subtype aggregator` das Hauptobjekt, das `project subtype project configuration` Objekt oder beides implementieren.

 In den folgenden Punkten werden die wichtigsten Konzepte für die Persistenz nicht buildbezogener Informationen beschrieben.

- Das Basisprojekt ruft das Aggregatorobjekt des Hauptprojekts (d. h. des äußersten Projektsubtyps) auf, um konfigurationsunabhängige Daten zu laden und zu speichern, und fordert die Projektuntertypkonfigurationsobjekte auf, konfigurationsabhängige Daten zu laden oder zu speichern.

- Das Basisprojekt ruft <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> die Methoden von mehreren Malen für jede Ebene der Projektsubtype-Aggregation auf und übergibt die GUID für jede Ebene.

- Das Basisprojekt übergibt oder empfängt ein XML-Fragment, das einem bestimmten Projektuntertyp gewidmet ist, und verwendet diesen Mechanismus als eine Möglichkeit, den Status zwischen den Aggregationsebenen beizubehalten.

- Das Basisprojekt ruft die Implementierung des <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>äußersten Projektsubtyps in einer GUID auf. Wenn die GUID zum untersten Projektsubtyp des äußersten Projekts gehört, verarbeitet sie den Aufruf selbst. Andernfalls delegiert er den Aufruf an einen inneren Projektuntertyp usw., bis der Projektuntertyp gefunden wird, dem die GUID entspricht.

- Ein Projektuntertyp kann auch das XML-Fragment ändern, bevor oder nachdem er den Aufruf an einen inneren Projektuntertyp delegiert. Das folgende Beispiel zeigt einen Auszug aus einer Projektdatei, in der ein Name einer Datei, die eigenschaften für einen Projektuntertyp enthält, an diesen Projektuntertyp übergeben wird.

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>Weitere Informationen
- [Projektuntertypen](../../extensibility/internals/project-subtypes.md)
