---
title: FileVersionInfo y StringFileInfo
date: 2020-11-20T11:24:09+00:00
draft: false
---
Cuando tenemos un proyecto de C++ en Visual Studio, existe un montón de información acerca del ejecutable que se incluye en él cómo es la versión del fichero y otra serie de parámetros que podemos necesitar en código.

Me he tenido que pegar con ello y aquí os dejo un par de ejemplos de uso de FileVersionInfo y StringVersionInfo con VerQueryValue y GetFileVersionInfo

## Ejemplo FileVersionInfo

<pre class="wp-block-code"><code>bool GetVersionInfo(
    LPCTSTR filename,
    int &major,
    int &minor,
    int &build,
    int &revision)
{
    DWORD   verBufferSize;
    char    verBuffer&#91;2048];

    //  Get the size of the version info block in the file
    verBufferSize = GetFileVersionInfoSize(filename, NULL);
    if(verBufferSize > 0 && verBufferSize &lt;= sizeof(verBuffer))
    {
        //  get the version block from the file
        if(TRUE == GetFileVersionInfo(filename, NULL, verBufferSize, verBuffer))
        {
            UINT length;
            VS_FIXEDFILEINFO *verInfo = NULL;

            //  Query the version information for neutral language
            if(TRUE == VerQueryValue(
                verBuffer,
                _T("\\"),
                reinterpret_cast&lt;LPVOID*>(&verInfo),
                &length))
            {
                //  Pull the version values.
                major = HIWORD(verInfo->dwProductVersionMS);
                minor = LOWORD(verInfo->dwProductVersionMS);
                build = HIWORD(verInfo->dwProductVersionLS);
                revision = LOWORD(verInfo->dwProductVersionLS);
                return true;
            }
        }
    }

    return false;
}</code></pre>

Es un ejemplo de <a href="https://stackoverflow.com/questions/6763262/c-get-version-from-rc-into-code" target="_blank" rel="noreferrer noopener">aquí</a>

## Ejemplo StringFileInfo

Éste ejemplo se complica porque necesitas saber el lenguaje de la máquina en la que se ejecuta pero este ejemplo es justo lo que neceistais:

<pre class="wp-block-code"><code>BOOL foo()
{
    const char* filename = "c:\\windows\\hh.exe";
    int dwLen = GetFileVersionInfoSize(filename, NULL);
    if(!dwLen)
        return 0;

    auto *sKey = new BYTE&#91;dwLen];
    std::unique_ptr&lt;BYTE&#91;]> skey_automatic_cleanup(sKey);
    if(!GetFileVersionInfo(filename, NULL, dwLen, sKey))
        return 0;

    struct LANGANDCODEPAGE {
        WORD wLanguage;
        WORD wCodePage;
    } *lpTranslate;

    UINT cbTranslate = 0;
    if(!VerQueryValue(sKey, "\\VarFileInfo\\Translation",
        (LPVOID*)&lpTranslate, &cbTranslate))
        return 0;

    for(unsigned int i = 0; i &lt; (cbTranslate / sizeof(LANGANDCODEPAGE)); i++)
    {
        char subblock&#91;256];
        //use sprintf if sprintf_s is not available
        sprintf_s(subblock, "\\StringFileInfo\\%04x%04x\\FileDescription",
            lpTranslate&#91;i].wLanguage, lpTranslate&#91;i].wCodePage);
        char *description = NULL;
        UINT dwBytes;
        if(VerQueryValue(sKey, subblock, (LPVOID*)&description, &dwBytes))
            MessageBox(0, description, 0, 0);
    }
    return TRUE;
}</code></pre>

Que es extraído de <a href="https://www.codeproject.com/Articles/8628/Retrieving-version-information-from-your-local-app" target="_blank" rel="noreferrer noopener">aquí</a>.

Happy codding!
