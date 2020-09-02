---
title: Elemente eines Projekt Modells | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700116"
---
# <a name="elements-of-a-project-model"></a>Elemente eines Projektmodells
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Schnittstellen und Implementierungen aller Projekte in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] haben eine grundlegende Struktur gemeinsam: das Projekt Modell für den Projekttyp. In Ihrem Projekt Modell, bei dem es sich um das VSPackage handelt, das Sie entwickeln, erstellen Sie Objekte, die ihren Entwurfsentscheidungen entsprechen und zusammen mit der von der IDE bereitgestellten globalen Funktionalität funktionieren. Obwohl Sie steuern, wie ein Projekt Element beibehalten wird, Steuern Sie z. b. die Benachrichtigung, dass eine Datei beibehalten werden muss. Wenn ein Benutzer den Fokus auf ein geöffnetes Projekt Element setzt und im Menü **Datei** in der Menüleiste die Option **Speichern** auswählt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , muss der Projekttyp Code den Befehl aus der IDE abfangen, die Datei persistent speichern und die Benachrichtigung an die IDE zurücksenden, dass die Datei nicht mehr geändert wird.  
  
 Das VSPackage interagiert mit der IDE über Dienste, die Zugriff auf die IDE-Schnittstellen bereitstellen. Beispielsweise können Sie über bestimmte Dienste Befehle überwachen und weiterleiten und Kontextinformationen für die im Projekt vorgenommenen Auswahl bereitstellen. Alle globalen IDE-Funktionen, die für Ihr VSPackage benötigt werden, werden von-Diensten bereitgestellt. Weitere Informationen zu Diensten finden Sie unter Gewusst [wie: erhalten eines Diensts](../../extensibility/how-to-get-a-service.md).  
  
 Weitere Überlegungen zur Implementierung:  
  
- Ein einzelnes Projekt Modell kann mehr als einen Projekttyp enthalten.  
  
- Projekttypen und die entsprechenden projektfactorys werden unabhängig von GUIDs registriert.  
  
- Jedes Projekt muss über eine Vorlagen Datei oder einen Assistenten verfügen, um die neue Projektdatei zu initialisieren, wenn ein Benutzer über die Benutzeroberfläche ein neues Projekt erstellt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Die [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] Vorlagen initialisieren z. b., was schließlich zu VCPROJ-Dateien wird.  
  
  Die folgende Abbildung zeigt die primären Schnittstellen, Dienste und Objekte, die eine typische Projekt Implementierung bilden. Sie können das Application Helper, HierUtil7, verwenden, um die zugrunde liegenden Objekte und andere Programmier Bausteine zu erstellen. Weitere Informationen zum HierUtil7-Anwendungs Hilfsprogramm finden [Sie unter nicht im Build: Verwenden von HierUtil7-Projektklassen zum Implementieren eines Projekt Typs (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
  ![Grafik zum Visual Studio-Projektmodell](../../extensibility/internals/media/vsprojectmodel.gif "vsprojectmodel")  
  Projektmodell  
  
  Weitere Informationen zu den im vorherigen Diagramm aufgelisteten Schnittstellen und Diensten sowie zu anderen optionalen Schnittstellen, die nicht im Diagramm enthalten sind, finden Sie unter [Projekt Modell-Kernkomponenten](../../extensibility/internals/project-model-core-components.md).  
  
  Projekte können Befehle unterstützen und müssen daher die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle implementieren, um am Befehls Routing über die Befehls Kontext-GUIDs teilnehmen zu können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Nicht im Build: Verwenden von HierUtil7-Projektklassen zum Implementieren eines Projekt Typs (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Projekt Modell-Kernkomponenten](../../extensibility/internals/project-model-core-components.md)   
 [Erstellen von Projekt Instanzen mithilfe von projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Vorgehensweise: erhalten eines Dienstanbieter](../../extensibility/how-to-get-a-service.md)   
 [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)
