---
title: "Gewusst wie: Migrieren eine domänenspezifischen Sprache zu einer neuen Version | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 14
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 397efd1049ea52b2e7c67a46509d2a088c6fa488
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Gewusst wie: Migrieren einer domänenspezifischen Sprache zu einer neuen Version
Sie können Projekte, definieren und Verwenden einer domänenspezifischen Sprache, migrieren [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] von der Version von [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , die mit verteilt wurde [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].  
  
 Ein Migrationstool dient als Teil des [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. Das Tool konvertiert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekte und Projektmappen, die verwendet oder DSL-Tools zu definieren.  
  
 Sie müssen explizit das Migrationstool ausführen: Es wird nicht automatisch gestartet, wenn Sie eine Projektmappe in öffnen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Das Tool und die ausführlichen Leitfaden finden Sie unter folgendem Pfad:  
  
 **% Programm Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>Vor dem Migrieren Sie Ihre DSL-Projekte  
 Ändert das Migrationstool [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projektdateien (**.csproj**) und Projektmappendateien (**.sln**).  
  
#### <a name="to-prepare-projects-for-migration"></a>Projekte für die Migration vorbereiten.  
  
-   Stellen Sie sicher, dass die **.csproj** und **.sln** Dateien können geschrieben werden. Verwaltet werden, stellen Sie sicher, dass sie ausgecheckt sind.  
  
-   Erstellen Sie eine Kopie der Ordner, die Sie migrieren möchten.  
  
## <a name="migrating-a-collection-of-projects"></a>Migrieren Sie eine Auflistung von Projekten  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Zum Migrieren von DSL-Projekte und Projektmappen zu Visual Studio 2010  
  
1.  Starten Sie das Migrationstool DSL.  
  
    -   Sie können Doppelklicken Sie auf das Tool in Windows Explorer (oder Datei-Explorer) oder das Tool von einer Befehlszeile aus starten. Das Tool ist an diesem Speicherort:  
  
         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  Wählen Sie einen Ordner mit Projektmappen und Projekten, die Sie konvertieren möchten.  
  
    -   Geben Sie den Pfad im Feld am oberen Rand des Tools ein, oder klicken Sie auf **Durchsuchen**.  
  
     Das Migrationstool zeigt eine Struktur von Projekten, die definieren, oder verwenden DSLs. Die Struktur enthält jedes Projekt, verwendet die **Microsoft.VisualStudio.Modeling.Sdk** oder **TextTemplating** Assemblys.  
  
3.  Überprüfen Sie die Struktur von Projekten, und deaktivieren Sie die Projekte, die Sie nicht konvertieren möchten.  
  
    -   Wählen Sie ein Projekt oder eine Projektmappe, um eine Liste der Änderungen anzuzeigen, mit denen das Tool.  
  
        > [!NOTE]
        >  Die Kontrollkästchen, die neben den Namen der Ordner angezeigt werden, haben keine Auswirkung. Erweitern Sie die Ordner, um Projekte und Projektmappen zu überprüfen.  
  
4.  Konvertieren Sie die Projekte.  
  
    1.  Klicken Sie auf **konvertieren**.  
  
         Vor jeder Projektdatei konvertiert, wird eine Kopie des *Projekt***.csproj** gespeichert ist, als *Projekt***. vs2008.csproj**  
  
         Eine Kopie aller *Lösung***.sln** gespeichert ist, als *Lösung***. vs2008.sln**  
  
    2.  Untersuchen Sie alle fehlerhaften Konvertierungen, die gemeldet werden.  
  
         Fehler werden im Textfenster angezeigt. Darüber hinaus wird die Strukturansicht ein Warnzeichen auf jedem Knoten, der nicht konvertieren konnte. Sie können den Knoten, um weitere Informationen zu diesem Fehler erhalten klicken.  
  
5.  **Transformieren aller Vorlagen** in Projektmappen mit erfolgreich Projekte konvertiert.  
  
    1.  Öffnen Sie die Projektmappe.  
  
    2.  Klicken Sie auf die **alle Vorlagen transformieren** Schaltfläche in der Kopfzeile des Projektmappen-Explorers.  
  
        > [!NOTE]
        >  Sie können diesen Schritt nicht erforderlich machen. Weitere Informationen finden Sie unter [wie alle Vorlagen transformieren automatisieren](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
6.  Aktualisieren Sie Ihren benutzerdefinierten Code in die konvertierte Projekte.  
  
    -   Versuchen Sie, die Projekte zu erstellen, und untersuchen Sie alle Fehler.  
  
    -   Testen Sie den Designer.  
  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Siehe auch  
 [Verwandte Blog-Einträge](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)


