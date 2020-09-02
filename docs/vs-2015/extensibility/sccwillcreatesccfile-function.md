---
title: Sccwillkreatesccfile-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb0df475098a0fb0675327cece6dd9c643a0c4d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147961"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion bestimmt, ob das Quellcodeverwaltungs-Plug-in die Erstellung von Mssccprj unterstützt. SCC-Datei für jede der angegebenen Dateien.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pContext  
 in Der Kontext Zeiger für das Quellcodeverwaltungs-Plug-in.  
  
 nnoch  
 in Die Anzahl von Dateinamen, die im Array enthalten sind, sowie `lpFileNames` die Länge des `pbSccFiles` Arrays.  
  
 lpfile-Namen  
 in Ein Array von voll qualifizierten Dateinamen, die überprüft werden sollen (das Array muss vom Aufrufer zugeordnet werden).  
  
 pbsccfiles  
 [in, out] Das Array, in dem die Ergebnisse gespeichert werden sollen.  
  
## <a name="return-value"></a>Rückgabewert  
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Erfolg.|  
|SCC_E_INVALIDFILEPATH|Einer der Pfade im Array ist ungültig.|  
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion wird mit einer Liste von Dateien aufgerufen, um zu bestimmen, ob das Quellcodeverwaltungs-Plug-in Unterstützung in Mssccprj bereitstellt. SCC-Datei für jede der angegebenen Dateien (Weitere Informationen zu Mssccprj. SCC-Datei finden Sie unter [Mssccprj. SCC-Datei](../extensibility/mssccprj-scc-file.md)). Quellcodeverwaltungs-Plug-Ins können deklarieren, ob Sie Mssccprj erstellen können. SCC-Dateien durch deklarieren `SCC_CAP_SCCFILE` während der Initialisierung. Das Plug-in gibt `TRUE` oder `FALSE` pro Datei im `pbSccFiles` Array zurück, um anzugeben, welche der angegebenen Dateien über Mssccprj verfügen. SCC-Unterstützung. Wenn das Plug-in einen Erfolgs Code aus der Funktion zurückgibt, werden die Werte im Rückgabe Array berücksichtigt. Bei einem Fehler wird das Array ignoriert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)   
 [Datei „MSSCCPRJ.SCC“](../extensibility/mssccprj-scc-file.md)
