---
title: 'Vorgehensweise: Migrieren eine domänenspezifischen Sprache zu einer neuen Version | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1d97e0204122e6dfcae89da7b04a0a303a0bd9a4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "47590602"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Gewusst wie: Migrieren einer domänenspezifischen Sprache zu einer neuen Version
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Migrieren einer domänenspezifischen Sprache zu einer neuen Version](https://docs.microsoft.com/visualstudio/modeling/how-to-migrate-a-domain-specific-language-to-a-new-version).  
  
Sie können Projekte, die definieren, und Verwenden einer domänenspezifischen Sprache migrieren [!INCLUDE[vs2010](../includes/vs2010-md.md)] von der Version der [!INCLUDE[dsl](../includes/dsl-md.md)] , die mit verteilt wurde [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].  
  
 Tool für die Migration erfolgt als Teil des [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)]. Das Tool konvertiert [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projekte und Projektmappen, die verwenden, oder definieren die DSL-Tools.  
  
 Sie müssen das Migrationstool explizit ausführen: Es wird nicht automatisch gestartet, wenn Sie eine Projektmappe in öffnen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Dokument mit den Tools und detaillierte Anleitungen finden Sie unter folgendem Pfad:  
  
 **% Programm Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>Vor dem Migrieren Sie Ihre DSL-Projekte  
 Ändert das Migrationstool [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projektdateien (**csproj**) und Projektmappendateien (**sln**).  
  
#### <a name="to-prepare-projects-for-migration"></a>Um Projekte für die Migration vorzubereiten.  
  
-   Stellen Sie sicher, dass die **csproj** und **sln** Dateien können geschrieben werden. Wenn sie sich unter quellcodeverwaltung sind, stellen Sie sicher, dass sie ausgecheckt sind.  
  
-   Erstellen Sie eine Kopie der Ordner, die Sie migrieren möchten.  
  
## <a name="migrating-a-collection-of-projects"></a>Migrieren Sie eine Sammlung von Projekten  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>DSL-Projekte und Projektmappen in Visual Studio 2010 migrieren  
  
1.  Starten Sie das Migrationstool DSL.  
  
    -   Sie können Doppelklicken Sie auf das Tool im Windows-Explorer (oder Datei-Explorer), oder Sie können das Tool an einer Eingabeaufforderung starten. Das Tool ist an diesem Speicherort:  
  
         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  Wählen Sie einen Ordner mit Projektmappen und Projekte, die Sie konvertieren möchten.  
  
    -   Geben Sie den Pfad in das Feld am oberen Rand des Tools, oder klicken Sie auf **Durchsuchen**.  
  
     Das Migrationstool zeigt eine Struktur von Projekten, die definieren, oder Verwenden von DSLs. Die Struktur enthält jedes Projekt, verwendet der **Microsoft.VisualStudio.Modeling.Sdk** oder **der TextTemplating** Assemblys.  
  
3.  Überprüfen Sie die Struktur von Projekten, und deaktivieren Sie die Projekte, die Sie nicht konvertieren möchten.  
  
    -   Wählen Sie ein Projekt oder eine Lösung, um eine Liste der Änderungen anzuzeigen, die das Tool machen werden.  
  
        > [!NOTE]
        >  Die Kontrollkästchen, die neben den Ordnernamen angezeigt werden, haben keine Auswirkungen. Erweitern Sie die Ordner, um die Projekte und Lösungen überprüfen.  
  
4.  Konvertieren Sie die Projekte an.  
  
    1.  Klicken Sie auf **konvertieren**.  
  
         Vor jede Projektdatei konvertiert wird, wird eine Kopie des _Projekt_**csproj** als gespeicherter _Projekt_**. vs2008.csproj**  
  
         Eine Kopie aller _Lösung_**sln** als gespeicherter _Lösung_**. vs2008.sln**  
  
    2.  Untersuchen Sie alle fehlerhaften Konvertierungen, die gemeldet werden.  
  
         Fehler werden im Textfenster gemeldet. Darüber hinaus wird der Strukturansicht ein Warnsignal, das auf jedem Knoten, die konvertiert werden konnte. Sie können den Knoten, um weitere Informationen zu diesem Fehler erhalten, klicken.  
  
5.  **Alle Vorlagen transformieren** in Lösungen, die erfolgreich enthält Projekte konvertiert.  
  
    1.  Öffnen Sie die Projektmappe.  
  
    2.  Klicken Sie auf die **alle Vorlagen transformieren** Schaltfläche im Header des Projektmappen-Explorer.  
  
        > [!NOTE]
        >  Sie können diesen Schritt nicht erforderlich machen. Weitere Informationen finden Sie unter [wie alle Vorlagen transformieren automatisieren](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
6.  Aktualisieren Sie Ihren benutzerdefinierten Code in die konvertierten Projekte ein.  
  
    -   Versuchen Sie, erstellen Sie die Projekte, und untersuchen Sie alle Fehler.  
  
    -   Testen Sie den Designer.  
  
## <a name="see-also"></a>Siehe auch  
 [Neues im Visualisierungs- und Modellierungs-SDK](../misc/what-s-new-in-visualization-and-modeling-sdk.md)



