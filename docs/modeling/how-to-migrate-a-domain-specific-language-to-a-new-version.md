---
title: "Vorgehensweise: Migrieren eine domänenspezifischen Sprache auf eine neue Version | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7f6aa84a55e629f003a1d9b896a5c095dc2d19ac
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Gewusst wie: Migrieren einer domänenspezifischen Sprache zu einer neuen Version
Sie können Projekte, definieren und Verwenden einer domänenspezifischen Sprache, migrieren [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] von der Version des [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , die mit verteilt wurde [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].  
  
 Ein Migrationstool dient als Teil des [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. Das Tool konvertiert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekte und Projektmappen, die verwenden oder DSL-Tools zu definieren.  
  
 Sie müssen das Migrationstool explizit ausführen: Es wird nicht automatisch gestartet, wenn Sie eine Projektmappe in öffnen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In diesem Pfad können das Tool und detaillierte Guidance-Dokument ermittelt werden:  
  
 **%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>Vor dem Migrieren Sie Ihre Projekte DSL  
 Ändert das Migrationstool [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projektdateien (**csproj**) und berichtsprojektmappen-Dateien (**sln**).  
  
#### <a name="to-prepare-projects-for-migration"></a>Projekte für die Migration vorbereitet.  
  
-   Stellen Sie sicher, dass die **csproj** und **sln** Dateien können geschrieben werden. Trifft dies in der quellcodeverwaltung, stellen Sie sicher, dass sie ausgecheckt sind.  
  
-   Erstellen Sie eine Kopie der Ordner, die Sie migrieren möchten.  
  
## <a name="migrating-a-collection-of-projects"></a>Migrieren Sie eine Auflistung von Projekten  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>DSL-Projekte und Projektmappen in Visual Studio 2010 zu migrieren  
  
1.  Starten Sie das Migrationstool DSL.  
  
    -   Sie können Doppelklicken Sie auf das Tool in Windows Explorer (oder Datei-Explorer), oder starten Sie das Tool über eine Eingabeaufforderung. Das Tool ist an diesem Speicherort:  
  
         **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  Wählen Sie einen Ordner mit Projektmappen und Projekten, die Sie konvertieren möchten.  
  
    -   Geben Sie den Pfad im Feld am oberen Rand des Tools ein, oder klicken Sie auf **Durchsuchen**.  
  
     Das Migrationstool zeigt eine Struktur von Projekten, die definieren, oder verwenden konzentriert. Die Struktur enthält jedes Projekt, verwendet der **Microsoft.VisualStudio.Modeling.Sdk** oder **TextTemplating** Assemblys.  
  
3.  Überprüfen Sie die Struktur von Projekten, und deaktivieren Sie die Projekte, die nicht konvertiert werden sollen.  
  
    -   Wählen Sie ein Projekt oder eine Projektmappe um eine Liste der Änderungen anzuzeigen, die das Tool erkennen lässt.  
  
        > [!NOTE]
        >  Die Kontrollkästchen, die neben den Ordnernamen angezeigt werden, haben keine Auswirkungen. Erweitern Sie den Ordner aus, um Projekte und Projektmappen zu überprüfen.  
  
4.  Konvertieren Sie die Projekte an.  
  
    1.  Klicken Sie auf **konvertieren**.  
  
         Vor jeder Projektdatei konvertiert wird, wird eine Kopie des *Projekt *** csproj** als gespeichert *Projekt ***.vs2008.csproj**  
  
         Eine Kopie der einzelnen *Lösung *** sln** als gespeichert *Lösung ***.vs2008.sln**  
  
    2.  Untersuchen Sie alle fehlerhaften Konvertierungen, die gemeldet werden.  
  
         Fehler werden im Fenster "den Text" gemeldet. Darüber hinaus wird die Strukturansicht ein Rot-Flag auf jedem Knoten, die zu konvertierende fehlgeschlagen ist. Sie können den Knoten, um weitere Informationen zu diesem Fehler erhalten klicken.  
  
5.  **Transformieren aller Vorlagen** in Projektmappen, die erfolgreich enthält Projekte konvertiert.  
  
    1.  Öffnen Sie die Projektmappe.  
  
    2.  Klicken Sie auf die **alle Vorlagen transformieren** Schaltfläche in der Kopfzeile des Projektmappen-Explorers.  
  
        > [!NOTE]
        >  Sie können diesen Schritt nicht erforderlich machen. Weitere Informationen finden Sie unter [wie alle Vorlagen transformieren automatisieren](http://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
6.  Aktualisieren Sie Ihren benutzerdefinierten Code in die konvertierten Projekte ein.  
  
    -   Versucht, die Projekte zu erstellen, und untersuchen Sie alle Fehler.  
  
    -   Testen Sie Ihren Designer.  
  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Siehe auch  
 [Verwandte Blogbeiträge](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

