---
title: "Beibehalten von Daten in der MSBuild-Projektdatei | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Beibehalten von Daten in Projektdateien."
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Beibehalten von Daten in der MSBuild-Projektdatei
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Projekt untertyp muss möglicherweise Untertyp spezifisch Daten in die Projektdatei für die spätere Verwendung beibehalten.  Ein Projekt untertyp Dauerhaftigkeit Projektdatei verwendet, um die folgenden Bedingungen erfüllen:  
  
1.  Behalten Sie die Daten, die als Teil der Erstellung des Projekts verwendet werden.  \(Weitere Informationen dazu finden Sie unter Microsoft Build Engine\). [MSBuild](http://msdn.microsoft.com/de-de/7c49aba1-ee6c-47d8-9de1-6f29a906e20b) Buildbezogene Informationen können folgende Möglichkeiten:  
  
    1.  konfigurationsunabhängige Daten.  Das bedeutet, Daten in MSBuild\-Elementen mit Leerzeichen oder fehlenden Bedingungen.  
  
    2.  Anlagenabhängige Daten.  Das bedeutet, Daten in MSBuild\-Elementen, die für eine bestimmte Projektkonfiguration bedungen werden.  Beispiele:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Beibehalten von Daten bei, das Erstellen nicht relevant ist.  Diese Daten können in der Freiform XML ausgedrückt werden, die nicht mit einem XML\-Schema überprüft wird.  
  
    1.  konfigurationsunabhängige Daten.  
  
    2.  Anlagenabhängige Daten.  
  
## Buildbezogene Informationen beibehalten  
 Dauerhaftigkeit von den Daten, die zum Erstellen eines Projekts nützlich sind, wird von MSBuild verarbeitet.  Das MSBuild\-System wartet eine Mastertabelle aus buildbezogenen Informationen.  Projekt untertypen sind zum Aufrufen dieser Daten zuständig, um Eigenschaftswerte abzurufen und festzulegen.  Projekt untertypen können die buildbezogene Datentabelle auch erweitern, indem sie die zusätzlichen beibehalten werden sollen und Eigenschaften hinzufügen, entfernen, deshalb werden diese Eigenschaften nicht beibehalten.  
  
 Um die MSBuild\-Bezugspunkte zu ändern, besteht ein Projekt untertyp zum Abrufen des MSBuild\-Eigenschaft Objekts vom Projektsystem der Basis <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>verantwortlich.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> ist eine Schnittstelle, die im zentralen Projektsystem und aggregierenden Projekt für Abfragen untertyp implementiert, indem es `QueryInterface`ausführt.  
  
 Im folgenden Verfahren werden die Schritte zum Entfernen einer Eigenschaft mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### So entfernen Sie eine Eigenschaft aus einer MSBuild\-Projektdatei  
  
1.  Rufen Sie `QueryInterface` auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> des Projekts untertyps an.  
  
2.  Aufrufs <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> mit `pszPropName` festgelegt auf die Eigenschaft, die Sie entfernen möchten.  
  
### Nicht\-Erstellung weitere Informationen beibehalten  
 Beibehaltung von Daten in den Projektdateien, die nicht der Fall ist, um zu erstellen, wird von <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>behandelt.  
  
 Sie können <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> auf dem primären `project subtype aggregator`\-Objekt, das `project subtype project configuration`\-Objekt oder beiden implementieren.  
  
 Die folgenden Punkte werden die wichtigsten Konzepte bezüglich der Beibehaltung von anderen Build nicht.  
  
-   Die grundlegenden Aufrufe Projekt auf dem primären Objekt vom Aggregator untertyps Projekt \(d. h. die äußerste Projekt untertyp\), um für unabhängige Daten der Konfiguration zu laden und zu speichern und rufen untertyp\-Projektkonfigurations Projekt auf Objekte an, die anlagenabhängige Daten zu laden und zu speichern.  
  
-   Das niedrige Projekt ruft die Methoden von <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> mehrmals für jede Ebene der Projekt untertyp aggregation an und führt die GUID für jede Ebene.  
  
-   Das niedrige Projekt wird oder empfängt ein XML\-Fragment, das einem bestimmten Projekt zugeordnet wird untertyp und verwendet diesen Mechanismus als Methode für die Verwaltung der Zustand zwischen den Ebenen Aggregations.  
  
-   Das niedrige Projekt ruft die äußersten des Projekts <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>Implementierung des Untertyps an, die in eine GUID.  Wenn die GUID des äußersten Projekt untertyp gehört, behandelt der Aufruf selbst. Andernfalls delegiert er den Aufruf eines inneren Projekt untertyp usw., bis der Projekt untertyp, dass die GUID entspricht, vorhanden ist.  
  
-   Ein Projekt untertyp kann das XML\-Fragment auch ändern, bevor oder nachdem er den Aufruf eines inneren Projekt untertyp delegiert.  Das folgende Beispiel einen Auszug aus einer Projektdatei, in der ein Name einer Datei, die die Eigenschaften enthält, die einem Projekt untertyp übergeben wird, gelten zu diesem Projekt untertyp anzeigt.  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## Siehe auch  
 [Projekt\-Untertypen](../../extensibility/internals/project-subtypes.md)