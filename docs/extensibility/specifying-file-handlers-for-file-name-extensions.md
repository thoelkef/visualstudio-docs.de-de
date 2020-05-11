---
title: Angeben von Dateihandlern für Dateinamenerweiterungen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af195aea09c91696843c6be42c20053bb8c095a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699758"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Angeben von Dateihandlern für Dateierweiterungen
Es gibt eine Reihe von Möglichkeiten, um die Anwendung zu bestimmen, die eine Datei verarbeitet, die eine bestimmte Dateierweiterung hat. Die Verben OpenWithList und OpenWithProgids sind zwei Möglichkeiten, Dateihandler unter dem Registrierungseintrag für die Dateierweiterung anzugeben.

## <a name="openwithlist-verb"></a>OpenWithList Verb
 Wenn Sie mit der rechten Maustaste auf eine Datei im Windows Explorer klicken, wird der Befehl **Öffnen** angezeigt. Wenn mehr als ein Produkt einer Erweiterung zugeordnet ist, wird ein Untermenü **"Öffnen mit"** angezeigt.

 Sie können verschiedene Anwendungen registrieren, um eine Erweiterung zu öffnen, indem Sie den OpenWithList-Schlüssel für die Dateierweiterung in HKEY_CLASSES_ROOT. Die unter diesem Schlüssel aufgeführten Anwendungen für eine Dateierweiterung werden unter der Überschrift **Empfohlene Programme** im Dialogfeld **"Mit öffnen"** angezeigt. Das folgende Beispiel zeigt die Anwendungen, die zum Öffnen der Dateierweiterung .vcproj registriert sind.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Die Schlüssel, die Anwendungen angeben, stammen aus der Liste unter HKEY_CLASSES_ROOT-Anwendungen.

 Durch Hinzufügen eines OpenWithList-Schlüssels erklären Sie, dass Ihre Anwendung eine Dateierweiterung unterstützt, auch wenn eine andere Anwendung den Besitz der Erweiterung übernimmt. Dies kann eine zukünftige Version Ihrer Anwendung oder eine andere Anwendung sein.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Programmgesteuerte Bezeichner (ProgIDs) sind benutzerfreundliche Versionen von ClassIDs, die eine Version einer Anwendung oder eines COM-Objekts identifizieren. Jedes ko-creaierbare Objekt sollte seine eigene ProgID haben. VisualStudio.DTE.7.1 startet beispielsweise Visual Studio .NET 2003, während VisualStudio.DTE.10.0 gestartet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]wird. Als Besitzer eines Projekttyps oder Projektelementtyps müssen Sie eine versionsspezifische ProgID für Ihre Dateierweiterung erstellen. Diese ProgIDs können redundant sein, da mehr als eine ProgID dieselbe Anwendung starten kann. Weitere Informationen finden Sie unter [Registrieren von Verben für Dateinamenerweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md).

 Verwenden Sie die folgende Namenskonvention für versionierte Datei-ProgIDs, um Doppelarbeit mit der Registrierung von anderen Anbietern zu vermeiden:

|Dateierweiterung|Versionierte ProgID|
|--------------------|----------------------|
|.extension|Productname. extension.versionMajor.versionMinor|

 Sie können verschiedene Anwendungen registrieren, die in der Lage sind, eine bestimmte Dateierweiterung\\zu öffnen, indem Sie versionierte ProgIDs als Werte zur*\<HKEY_CLASSES_ROOT-Erweiterung>*-OpenWithProgids-Schlüssel hinzufügen. Dieser Registrierungsschlüssel enthält eine Liste alternativer ProgIDs, die der Dateierweiterung zugeordnet sind. Die Anwendungen, die den aufgeführten ProgIDs zugeordnet sind, werden im Untermenü **"Öffnen mit**_Produktname"_ angezeigt. Wenn dieselbe Anwendung sowohl im `OpenWithList` `OpenWithProgids` Schlüssel als auch in den Schlüsseln angegeben ist, führt das Betriebssystem die Duplikate zusammen.

> [!NOTE]
> Der `OpenWithProgids` Schlüssel wird nur in Windows XP unterstützt. Da andere Betriebssysteme diesen Schlüssel ignorieren, verwenden Sie ihn nicht als einzige Registrierung für Dateihandler. Verwenden Sie diesen Schlüssel, um eine bessere Benutzererfahrung in Windows XP zu ermöglichen.

 Fügen Sie die gewünschten ProgIDs als Werte des Typs REG_NONE hinzu. Der folgende Code enthält ein Beispiel für die Registrierung von ProgIDs für eine Dateierweiterung (.* ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 Die ProgID, die als Standardwert für die Dateierweiterung angegeben ist, ist der Standarddateihandler. Wenn Sie die ProgID für eine Dateierweiterung ändern, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die mit einer früheren Version von geliefert `OpenWithProgids` wurde oder von anderen Anwendungen übernommen werden kann, müssen Sie den Schlüssel für Ihre Dateierweiterung registrieren und die neue ProgID in der Liste zusammen mit den alten ProgIDs angeben, die Sie unterstützen. Beispiel:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Wenn der alten ProgID Verben zugeordnet sind, werden diese Verben auch unter Mit *Produktname* **öffnen** im Kontextmenü angezeigt.

## <a name="see-also"></a>Weitere Informationen
- [Informationen zu Dateierweiterungen](../extensibility/about-file-name-extensions.md)
- [Registrieren von Verben für Dateierweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md)
