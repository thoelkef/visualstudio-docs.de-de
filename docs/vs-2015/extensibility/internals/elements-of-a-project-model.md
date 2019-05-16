---
title: Elemente eines Projektmodells | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3b07068939e34b5c9e9487761177c0e12f5654
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700116"
---
# <a name="elements-of-a-project-model"></a>Elemente eines Projektmodells
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Schnittstellen und Implementierungen aller Projekte in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Teilen eine Grundstruktur: das Modell für den Projekttyp. In Ihrem Projektmodell, das das VSPackage ist, Sie entwickeln, erstellen Sie die Objekte, die Ihre entwurfsentscheidungen entsprechen und zusammen mit globalen Funktionen, die von der IDE bereitgestellt. Auch wenn Sie steuern, wie ein Projektelement beibehalten wird, können z. B. Sie keine Benachrichtigung steuern, dass eine Datei beibehalten werden muss. Wenn ein Benutzer setzt den Fokus auf ein Projektelement öffnen, und wählt **speichern** auf die **Datei** Menü auf der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Menü, Typ Projektcode abfangen, den Befehl in der IDE, speichern Sie die Datei muss und Senden Sie Benachrichtigungen zurück zur IDE, dass die Datei nicht mehr geändert wird.  
  
 Das VSPackage interagiert mit der IDE über Dienste, die Zugriff auf die IDE-Schnittstellen bereitstellen. Z. B. über bestimmte Dienste, überwachen und die Route-Befehle, und bieten Kontextinformationen für die Auswahl, die im Projekt. Alle globalen den Funktionsumfang der IDE erforderlich sind, für das VSPackage wird von Diensten bereitgestellt. Weitere Informationen zu Diensten finden Sie unter [Vorgehensweise: Abrufen eines Diensts](../../extensibility/how-to-get-a-service.md).  
  
 Andere Aspekte der Implementierung:  
  
- Ein einzelnes Projekt-Modell kann mehr als ein Projekt enthalten.  
  
- Projekttypen und die zugehörige projektfactorys werden unabhängig voneinander mit GUIDs registriert.  
  
- Jedes Projekt benötigen eine Vorlagendatei oder einen Assistenten, um die neue Projektdatei zu initialisieren, wenn ein Benutzer über ein neues Projekt erstellt die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Benutzeroberfläche. Z. B. die [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] Vorlagen zu initialisieren, was schließlich VCPROJ-Dateien werden.  
  
  Die folgende Abbildung zeigt die primären Schnittstellen, Dienste und Objekte, die eine Implementierung der typischen Projekt zu erstellen. Die Anwendung Hilfsprogramms, des HierUtil7, können Sie um die zugrunde liegenden Objekte und andere Programmiersprachen Codebausteinen zu erstellen. Weitere Informationen zu der Anwendung HierUtil7-Hilfsprogramm, finden Sie unter [nicht im Build: HierUtil7-Projektklassen zum Implementieren eines Projekttyps (C++) mit](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
  ![Grafik zum Visual Studio-Projektmodell](../../extensibility/internals/media/vsprojectmodel.gif "VsProjectModel")  
  Projektmodell  
  
  Weitere Informationen über die Schnittstellen und Dienste, die im vorherigen Diagramm und andere optionalen Schnittstellen, die nicht im Diagramm enthalten, finden Sie unter [Hauptkomponenten eines Projektmodells](../../extensibility/internals/project-model-core-components.md).  
  
  Projekte können Befehle unterstützen und daher implementieren, muss die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle, um das Befehlsrouting über den Befehlskontext GUIDs teilnehmen.  
  
## <a name="see-also"></a>Siehe auch  
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Nicht im Build: Mithilfe von HierUtil7 Projektklassen zum Implementieren eines Projekttyps (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Hauptkomponenten eines Projektmodells](../../extensibility/internals/project-model-core-components.md)   
 [Erstellen von Projektinstanzen mithilfe von Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Vorgehensweise: Abrufen eines Diensts](../../extensibility/how-to-get-a-service.md)   
 [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)
