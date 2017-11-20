---
title: "Vorgehensweise: hinzufügen eine Abhängigkeit zu einem VSIX-Paket | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3f3b54e19d8418f35a733b73ea0616b53bd42ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Vorgehensweise: hinzufügen eine Abhängigkeit zu einem VSIX-Paket
Sie können ein VSIX-Paket-Bereitstellung einrichten, die alle Abhängigkeiten installiert wird, die noch nicht auf dem Zielcomputer vorhanden sind. Um dies zu erreichen, enthalten Sie die VSIX-Abhängigkeiten in der Datei "Source.Extension.vsixmanifest".  
  
#### <a name="to-add-a-dependency"></a>Hinzufügen eine Abhängigkeit  
  
1.  Öffnen Sie die Datei "Source.Extension.vsixmanifest" in der **Entwurf** anzeigen. Wechseln Sie zu der **Abhängigkeiten** Registerkarte, und klicken Sie auf **neu**.  
  
2.  Zum Hinzufügen einer installierten Erweiterungs: in der **neue Abhängigkeit hinzufügen** wählen Sie im Dialogfeld **-Erweiterung installiert** und schließlich für den **Namen**, wählen Sie eine Erweiterung in der Liste.  
  
3.  Eine andere VSIX hinzuzufügen, die nicht installiert ist:: in der **neue Abhängigkeit hinzufügen** wählen Sie im Dialogfeld **Dateisystem** und verwenden Sie dann die **Durchsuchen** klicken, um die VSIX auszuwählen.  
  
## <a name="see-also"></a>Siehe auch  
 [VSIX-Erweiterung Schemareferenz 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Aufbau eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [Vorbereiten von Erweiterungen für die Windows Installer-Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md)