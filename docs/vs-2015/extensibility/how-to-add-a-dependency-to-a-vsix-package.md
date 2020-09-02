---
title: 'Vorgehensweise: Hinzufügen einer Abhängigkeit zu einem VSIX-Paket | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 997c0df133b72d69dfb4e69de53a1b77e1a0965c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697507"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Gewusst wie: Hinzufügen einer Abhängigkeit zu einem VSIX-Paket
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine VSIX-Paket Bereitstellung einrichten, mit der alle Abhängigkeiten installiert werden, die nicht bereits auf dem Zielcomputer vorhanden sind. Fügen Sie hierzu die VSIX-Abhängigkeiten in die Datei "Source. Extension. vsixmanifest" ein.  
  
#### <a name="to-add-a-dependency"></a>So fügen Sie eine Abhängigkeit hinzu  
  
1. Öffnen Sie die Datei "Source. Extension. vsixmanifest" in der **Entwurfs** Ansicht. Wechseln Sie zur Registerkarte **Abhängigkeiten** , und klicken Sie auf **neu**.  
  
2. So fügen Sie eine installierte Erweiterung hinzu: Wählen Sie im Dialogfeld **neue Abhängigkeit hinzufügen** die Option **installierte Erweiterung** aus, und wählen Sie dann als **Name**eine Erweiterung in der Liste aus.  
  
3. Zum Hinzufügen einer weiteren VSIX, die nicht installiert ist:: Wählen Sie im Dialogfeld **neue Abhängigkeit hinzufügen** die Option **Datei im Dateisystem** aus, und wählen Sie dann die VSIX mithilfe der Schaltfläche **Durchsuchen** aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSIX-Erweiterungs Schema 1,0-Referenz](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [Vorbereiten von Erweiterungen für die Windows Installer-Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
