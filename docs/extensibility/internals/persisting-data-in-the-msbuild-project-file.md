---
title: Beibehalten von Daten in der MSBuild-Projektdatei | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7772f633c44c50b24995b7cc8a3f2f8bbbb01863
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726056"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Beibehalten von Daten in der MSBuild-Projektdatei
Ein Projekt Untertyp muss möglicherweise Untertyp spezifische Daten für die spätere Verwendung in der Projektdatei beibehalten. Ein Projekt Untertyp verwendet die Persistenz von Projektdateien, um die folgenden Anforderungen zu erfüllen:

1. Beibehalten von Daten, die beim Projekt Aufbau verwendet werden. (Weitere Informationen zum Microsoft-Build-Engine finden Sie unter [MSBuild](../../msbuild/msbuild.md).) Buildbezogene Informationen können folgende Aktionen ausführen:

    1. Konfigurations unabhängige Daten. Das heißt, Daten, die in MSBuild-Elementen mit leeren oder fehlenden Bedingungen gespeichert werden.

    2. Konfigurations abhängige Daten. Das heißt, dass Daten in MSBuild-Elementen gespeichert werden, die für eine bestimmte Projekt Konfiguration bedingt sind. Beispiel:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Speichert Daten, die für die Erstellung nicht relevant sind. Diese Daten können in frei Form-XML ausgedrückt werden, das nicht anhand eines XML-Schemas überprüft wird.

    1. Konfigurations unabhängige Daten.

    2. Konfigurations abhängige Daten.

## <a name="persisting-build-related-information"></a>Beibehalten von buildbezogenen Informationen
 Die Persistenz von Daten, die zum Erstellen eines Projekts hilfreich sind, wird über MSBuild behandelt. Das MSBuild-System verwaltet eine Master Tabelle mit Build-bezogenen Informationen. Projekt Untertypen sind für den Zugriff auf diese Daten verantwortlich, um Eigenschaftswerte zu erhalten und festzulegen. Projekt Untertypen können die Build-bezogene Datentabelle auch erweitern, indem Sie zusätzliche Eigenschaften hinzufügen, die persistent gespeichert werden sollen, und indem Sie Eigenschaften entfernen, sodass Sie nicht persistent sind.

 Um die MSBuild-Daten zu ändern, ist ein Projekt Untertyp für das Abrufen des MSBuild-Eigenschafts Objekts aus dem Basisprojekt System über <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> verantwortlich. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> ist eine Schnittstelle, die auf dem Hauptprojekt System implementiert ist, und die aggregierten Projekt Untertypen Abfragen dafür durch Ausführen von `QueryInterface`.

 Im folgenden Verfahren werden die Schritte zum Entfernen einer Eigenschaft mithilfe <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> erläutert.

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>So entfernen Sie eine Eigenschaft aus einer MSBuild-Projektdatei

1. Ruft `QueryInterface` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> des Projekt unter Typs auf.

2. Ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> auf, bei dem `pszPropName` auf die Eigenschaft festgelegt ist, die Sie entfernen möchten.

### <a name="persisting-non-build-related-information"></a>Beibehalten von nicht Build bezogenen Informationen
 Die Persistenz von Daten in Projektdateien, die für die Erstellung keine Rolle spielen, wird durch <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> behandelt.

 Sie können <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> auf dem Haupt `project subtype aggregator` Objekt, dem `project subtype project configuration`-Objekt oder beides implementieren.

 Die folgenden Punkte beschreiben die Hauptkonzepte bezüglich der Persistenz von Informationen, die nicht im Build zusammenhängen.

- Das Basisprojekt Ruft für den Hauptprojekt Untertyp (d. h. das äußerste Projekt Untertyp) Aggregator-Objekt auf, um die Konfigurations unabhängigen Daten zu laden und zu speichern, und ruft für die Projekt Untertypen Projekt-Konfigurationsobjekte auf, um Konfigurations abhängige Daten zu laden oder zu speichern. Vorrats.

- Das Basisprojekt Ruft die Methoden von <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> mehrmals für jede Ebene der Projekt Untertypen Aggregation auf und übergibt die GUID für jede Ebene.

- Das Basisprojekt übergibt oder empfängt ein XML-Fragment, das einem bestimmten Projekt Untertyp zugeordnet ist, und verwendet diesen Mechanismus als Möglichkeit zum Beibehalten des Zustands zwischen den Aggregations Ebenen.

- Das Basisprojekt Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementation des äußeren Projekt unter Typs auf, wobei eine GUID übergeben wird. Wenn die GUID zum äußersten Projekt Untertyp gehört, wird der eigentliche Rückruf behandelt. Andernfalls wird der-Aufrufe an einen inneren Projekt Untertyp delegiert usw., bis der Projekt Untertyp gefunden wird, dem die GUID entspricht.

- Ein Projekt Untertyp kann das XML-Fragment auch vor oder nach dem Delegaten des Aufrufes an einen inneren Projekt Untertyp ändern. Das folgende Beispiel zeigt einen Auszug aus einer Projektdatei, bei der der Name einer Datei, die Eigenschaften enthält, die für einen Projekt Untertyp spezifisch sind, an diesen Projekt Untertyp übermittelt wird.

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>Siehe auch
- [Projektuntertypen](../../extensibility/internals/project-subtypes.md)