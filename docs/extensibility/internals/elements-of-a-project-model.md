---
title: Elemente eines Modells Projekt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4933e73df93c1f8a3bcf62e03b6883c0096f1d8f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135558"
---
# <a name="elements-of-a-project-model"></a>Elemente eines Projekt-Modells
Die Schnittstellen und Implementierungen aller Projekte in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Teilen Sie Basisstruktur: das Projektmodell für den Projekttyp. In Ihrem Projektmodell, das das VSPackage ist, Sie entwickeln, erstellen Sie Objekte, die gemeinsam mit globalen Funktionen, die von der IDE bereitgestellt und mit entwurfsentscheidungen übereinstimmen. Obwohl Sie steuern, wie ein Projektelement beibehalten wird, können z. B. Sie keine Benachrichtigung gesteuert werden, dass eine Datei beibehalten werden muss. Wenn ein Benutzer den Fokus auf ein Projekt öffnen Element platziert und wählt **speichern** auf die **Datei** Menü auf die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Menü Projektcode Typ muss Balken-, den Befehl in der IDE abzufangen, persistent speichern die Datei und Benachrichtigungen der IDE an, dass die Datei nicht mehr geändert wird.  
  
 Das VSPackage interagiert mit der IDE über Dienste, die Zugriff auf die IDE-Schnittstellen bereitstellen. Z. B. über bestimmte Dienste überwachen und die Routenwerte Befehle zu Kontextinformationen für die Auswahl im Projekt bereitstellen. Alle globalen IDE benötigten Funktionen für das VSPackage wird von Diensten bereitgestellt. Weitere Informationen zu Diensten finden Sie unter [Vorgehensweise: Abrufen eines Diensts](../../extensibility/how-to-get-a-service.md).  
  
 Andere Aspekte der Implementierung:  
  
-   Ein einzelnes Projekt-Modell kann mehrere Projekttyp enthalten.  
  
-   Projekttypen und das zugehörige projektfactorys werden unabhängig voneinander GUIDs registriert.  
  
-   Jedes Projekt muss einer Vorlagendatei oder den Assistenten, um die neue Projektdatei zu initialisieren, wenn ein Benutzer über ein neues Projekt erstellt haben die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] UI. Z. B. die [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Vorlagen zu initialisieren, was schließlich .vcproj-Dateien werden.  
  
 Die folgende Abbildung zeigt den primären Schnittstellen, Diensten und Objekten, die eine typischen Projekt Implementierung bilden. Die Anwendung Hilfsprogramms, des HierUtil7, können Sie die zugrunde liegenden Objekte und anderen Programmiersprachen Textbaustein erstellen. Weitere Informationen zu der Anwendung HierUtil7-Hilfsprogramm, finden Sie unter [nicht im Build: verwenden HierUtil7 Projektklassen zum Implementieren von einem Project-Typs (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
 ![Grafik zu Visual Studio-Projektmodell](../../extensibility/internals/media/vsprojectmodel.gif "VsProjectModel")  
Projektmodell  
  
 Weitere Informationen über die Schnittstellen und in der vorherigen Abbildung aufgeführten Dienste und andere optionalen Schnittstellen, die nicht im Diagramm enthalten, finden Sie unter [Projekt Modell Kernkomponenten](../../extensibility/internals/project-model-core-components.md).  
  
 Projekte können Befehle unterstützen und daher implementieren, müssen die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle Befehlsrouting über den Befehlskontext GUIDs teilnehmen.  
  
## <a name="see-also"></a>Siehe auch  
 [Prüfliste: Erstellen neuen Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Nicht im Build: Verwenden von HierUtil7 Projektklassen zum Implementieren von eines Projekttyps (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Projekt-Modell-Kernkomponenten](../../extensibility/internals/project-model-core-components.md)   
 [Erstellen von Instanzen von Project mithilfe von Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Vorgehensweise: Abrufen eines Diensts](../../extensibility/how-to-get-a-service.md)   
 [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)