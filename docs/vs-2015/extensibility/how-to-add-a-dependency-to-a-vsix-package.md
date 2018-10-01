---
title: 'Vorgehensweise: hinzufügen eine Abhängigkeit zu einem VSIX-Paket | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ebd835fef9df8fbdeb67bdf9c7e6eff31bcf4730
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521604"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Vorgehensweise: hinzufügen eine Abhängigkeit zu einem VSIX-Paket
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: hinzufügen eine Abhängigkeit zu VSIX Package](https://docs.microsoft.com/visualstudio/extensibility/how-to-add-a-dependency-to-a-vsix-package).  
  
Sie können eine VSIX-Paket-Bereitstellung einrichten, die alle Abhängigkeiten installiert, die noch nicht auf dem Zielcomputer vorhanden sind. Gehören Sie zu diesem Zweck die VSIX-Abhängigkeiten in die Datei "Source.Extension.vsixmanifest" ein.  
  
#### <a name="to-add-a-dependency"></a>Eine Abhängigkeit hinzufügen  
  
1.  Öffnen Sie die Datei "Source.Extension.vsixmanifest" in der **Entwurf** anzeigen. Wechseln Sie zu der **Abhängigkeiten** Registerkarte, und klicken Sie auf **neu**.  
  
2.  Um eine installierte Erweiterung hinzuzufügen: in der **neue Abhängigkeit hinzufügen** wählen Sie im Dialogfeld **-Erweiterung installiert** dann für die **Namen**, wählen Sie eine Erweiterung in der Liste.  
  
3.  Eine andere VSIX hinzufügen, die nicht installiert ist:: in der **neue Abhängigkeit hinzufügen** wählen Sie im Dialogfeld **Dateisystem** und verwenden Sie dann die **Durchsuchen** klicken, um die VSIX-Datei auszuwählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zum VSIX-Erweiterung Schema 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [Vorbereiten von Erweiterungen für die Windows Installer-Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md)

