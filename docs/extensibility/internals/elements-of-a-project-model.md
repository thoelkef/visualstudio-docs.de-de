---
title: "Elemente eines Projektmodells | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekte [Visual Studio SDK] Aspekte der Implementierung"
  - "Projektmodelle"
  - "Projekte [Visual Studio SDK] Elemente"
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Elemente eines Projektmodells
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Schnittstellen und den Implementierungen aller Projekte in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geben eine grundlegende Struktur frei: das Projektmodell für den Projekttyp.  Klicken Sie im Projektmodell VSPackage ist, das Sie entwickeln, erstellen Sie die Objekte, die den betreffenden Entscheidungen Entwurf zusammen mit der Arbeit und globale Funktionen entsprechen, die in der IDE bereitgestellt wird.  Obwohl Sie steuern, wie ein Projektelement gespeichert werden, z. B. Gehen Sie nicht Steuerelementbenachrichtigung, dass eine Datei beibehalten werden muss.  Wenn ein Benutzer den Fokus in einem geöffneten Projektelement gespeichert und **Speichern** auf dem **Datei** Menü auf der Menüleiste [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekttyp auswählen, muss der Code den Befehl über die IDE abfangen, besteht die Datei weiter und sendet eine Benachrichtigung an die IDE, dass die Datei nicht mehr geändert wird.  
  
 VSPackage interagiert mit der IDE über Dienste, die den Zugriff auf IDE\-Schnittstellen ermöglichen.  Zum Beispiel von bestimmten Diensten, und überwachen Sie Befehle ausführen und stellen weitere Kontextinformationen für die Auswahl bereit, die im Projekt erstellt wird.  Die gesamte globale IDE\-Funktionalität, die für ein VSPackage benötigt wird, wird von den Diensten bereitgestellt.  Weitere Informationen zu Diensten finden Sie unter [Gewusst wie: Abrufen eines Diensts](../../extensibility/how-to-get-a-service.md).  
  
 Andere Überlegungen zur Implementierung:  
  
-   Ein einzelnes Projektmodell kann mehr als einen Projekttyp enthalten.  
  
-   Projekttypen und den begleitenden Projekt factorys werden unabhängig mit GUIDs registriert.  
  
-   Jedes Projekt muss eine Vorlagendatei oder einen Assistenten verwenden, um die neue Projektdatei zu initialisieren, wenn ein Benutzer ein neues Projekt vom [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche erstellt.  Zum Beispiel initialisieren die [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Vorlagen, was schließlich .vcproj\-Dateien werden.  
  
 Die folgende Abbildung zeigt die wichtigsten Schnittstellen, die Dienste und die Objekte an, die eine typische Projektdurchführung zusammensetzt.  Sie können die Anwendung können, HierUtil7 verwenden, um die zugrunde liegenden Objekte und anderen Programmierung vorformulierten Satz zu erstellen.  Weitere Informationen über die Verwendung der Hilfe HierUtil7 finden Sie unter [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/de-de/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
 ![Grafik zum Visual Studio&#45;Projektmodell](~/docs/extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
Projektmodell  
  
 Weitere Informationen zu den Schnittstellen und Dienste, die im vorherigen Diagramm aufgeführt sind, und anderen optionalen Schnittstellen, die nicht im Diagramm eingeschlossen werden, finden Sie unter [Projekt\-Modell\-Kernkomponenten](../../extensibility/internals/project-model-core-components.md).  
  
 Projekte können Befehle unterstützen und daher müssen die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\-Schnittstelle implementieren, um am Befehls routing durch den Befehl Elementkontext GUID teilzunehmen.  
  
## Siehe auch  
 [Prüfliste: Erstellen von neuen Typen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/de-de/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Projekt\-Modell\-Kernkomponenten](../../extensibility/internals/project-model-core-components.md)   
 [Erstellen von Instanzen von Project mithilfe von Project\-Factorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Gewusst wie: Abrufen eines Diensts](../../extensibility/how-to-get-a-service.md)   
 [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)