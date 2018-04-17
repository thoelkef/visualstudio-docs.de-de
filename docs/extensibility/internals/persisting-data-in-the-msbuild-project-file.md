---
title: Beibehalten von Daten in der MSBuild-Projektdatei | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 324f9dfd4e381e9580e4940f06f652ef64d9d3ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Beibehalten von Daten in der MSBuild-Projektdatei
Ein Projektuntertyp möglicherweise untertypspezifischen Daten in der Projektdatei zur späteren Verwendung beizubehalten. Ein Projektuntertyp verwendet projektdauerhaftigkeit-Datei, um die folgenden Anforderungen erfüllen:  
  
1.  Beibehalten von Daten, die als Teil der Erstellung des Projekts verwendet. (Weitere Informationen zu Microsoft Build Engine, finden Sie unter [MSBuild](../../msbuild/msbuild.md).) Buildbezogene Informationen kann entweder:  
  
    1.  Unabhängige Konfiguration Daten. D. h. in MSBuild-Elemente mit leeren oder fehlenden Bedingungen gespeicherten Daten.  
  
    2.  Die konfigurationsabhängigen Daten. D. h. in MSBuild-Elemente, die für einen bestimmten Projektkonfiguration abhängig davon sind gespeicherten Daten. Zum Beispiel:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Beibehalten von Daten, die für das Erstellen nicht relevant ist. Diese Daten können im Freiform-XML-Format ausgedrückt werden, die nicht für ein XML-Schema überprüft wird.  
  
    1.  Unabhängige Konfiguration Daten.  
  
    2.  Die konfigurationsabhängigen Daten.  
  
## <a name="persisting-build-related-information"></a>Buildbezogene Informationen beibehalten  
 Dauerhaftigkeit der Daten nützlich zur Erstellung eines Projekts erfolgt über MSBuild. Das MSBuild-System verwaltet eine Mastertabelle mit buildbezogene Informationen. Projekt Untertypen sind verantwortlich für den Zugriff auf diese Daten zum Abrufen und Festlegen von Eigenschaftswerten. Projekt Untertypen ergänzen können auch buildbezogene Datentabelle durch Hinzufügen von zusätzlichen Eigenschaften, die beibehalten werden und Eigenschaften zu entfernen, damit sie nicht persistent gespeichert werden.  
  
 Um die MSBuild-Daten zu ändern, ist ein Projektuntertyp verantwortlich zum Abrufen von MSBuild-Property-Objekt aus der Basisprojektsystem über <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> ist eine für taskklassen implementierte Schnittstelle Projektsystem Core und aggregieren Projekt Untertyp Abfragen dafür Treiberdienst `QueryInterface`.  
  
 Das folgende Verfahren erläutert die Schritte zum Entfernen einer Eigenschaft mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>So entfernen Sie eine Eigenschaft aus einer MSBuild-Projektdatei  
  
1.  Rufen Sie `QueryInterface` auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> der Untertyp des Projekts.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> mit `pszPropName` Festlegen der Eigenschaft, die Sie entfernen möchten.  
  
### <a name="persisting-non-build-related-information"></a>Beibehalten von nicht-Build-Informationen  
 Dauerhaftigkeit der Daten in Projektdateien, die keine Rolle spielt erstellen erfolgt über <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.  
  
 Sie implementieren können <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> auf der Hauptseite `project subtype aggregator` -Objekt, das `project subtype project configuration` Objekt oder beides.  
  
 Die folgenden Punkte beschreiben die wichtigsten Konzepte hinsichtlich der Persistenz verwandter Informationen nicht erstellen.  
  
-   Das Basisprojekt aufruft, für das Hauptprojekt Untertyp (d. h. die äußerste Projektuntertyp) Aggregator Objekt zu laden und Speichern von Konfigurationsdaten unabhängig, und er ruft für das Projekt Untertyp Projekt Konfigurationsobjekte zum Laden und speichern abhängig von der Konfiguration Daten.  
  
-   Das Basisprojekt Ruft die Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> mehrere für jede Ebene der Projekt-Untertyp Aggregation dreimal auf und übergibt die GUID für jede Ebene.  
  
-   Die Basisprojekt übergibt oder empfängt XML-Fragment, das für ein bestimmtes Projektuntertyp dediziert ist und dieser Mechanismus als eine Möglichkeit, Beibehaltung des Status zwischen den Aggregationsebenen verwendet.  
  
-   Das Basisprojekt ruft des äußersten Projekt Untertyps <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>Implementierung, die in eine GUID übergeben. Wenn die GUID zu den Projektuntertyp äußersten gehört, behandelt den Aufruf selbst; Andernfalls wird der Aufruf delegiert, eine innere Projektuntertyp usw., bis der Projektuntertyp, dem die GUID entspricht gefunden wird.  
  
-   Ein Projektuntertyp kann auch das XML-Fragment ändern, vor oder nach dem Aufruf von einem inneren Projektuntertyp delegiert. Das folgende Beispiel zeigt einen Auszug aus einer Projektdatei, bei dem ein Name einer Datei, die einen Projektuntertyp spezifischen Eigenschaften enthält in diesem Projektuntertyp übergeben wird.  
  
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
 [Projektuntertypen](../../extensibility/internals/project-subtypes.md)