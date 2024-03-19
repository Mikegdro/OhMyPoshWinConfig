## Configuración de OhMyPosh

OhMyPosh es una aplicación que nos permite customizar el terminal de windows para ponerlo bien bacano y bonico.

Esto asume que ya tienes instalado OhMyPosh en tu sistema.

### PowerShell
En este repo hay dos archivos, el archivo de configuración de powershell, que para instalarlo tenemos que invocar 
el visual studio code al perfil de windows con el comando:

```powershell
code $PROFILE
```

Copiamos y pegamos el contenido del archivo del repo y podemos pasar al siguiente paso.

### Tema de OhMyPosh

Para configurar el tema si hacemos un:

```powershell
cat $env:POSH_THEMES_PATH
```

Podremos ver la ruta de los temas instalados, en este caso el tema que tenemos personalizado es agnosterplus.

Vamos a la carpeta que nos especifica la ruta de themes, y buscamos el archivo agnosterplus.omp.json, y copiamos y pegamos el contenido del documento.

Lo más importante es el siguiente fragmento:

```json

    {
            "background": "#95ffa4",
            "foreground": "#193549",
            "background_templates": [
            "{{ if or (.Working.Changed) (.Staging.Changed) }}#FFEB3B{{ end }}",
            "{{ if and (gt .Ahead 0) (gt .Behind 0) }}#FFCC80{{ end }}",
            "{{ if gt .Ahead 0 }}#B388FF{{ end }}",
            "{{ if gt .Behind 0 }}#B388FB{{ end }}"
            ],
            "powerline_symbol": "\ue0b0",
            "style": "powerline",
            "template": "{{ .UpstreamIcon }}{{ .HEAD }}{{if .BranchStatus }} {{ .BranchStatus }}{{ end }}{{ if .Working.Changed }}  {{ .Working.String }}{{ end }}{{ if and (.Working.Changed) (.Staging.Changed) }} |{{ end }}{{ if .Staging.Changed }}  {{ .Staging.String }}{{ end }}{{ if gt .StashCount 0 }}  {{ .StashCount }}{{ end }}",
            "type": "git",
            "properties": {
            "fetch_status": true,
            "fetch_stash_count": true,
            "fetch_upstream_icon": true,
            "untracked_modes": {
                "/Users/user/Projects/oh-my-posh/": "no"
            }
        }
    }

```

En el objeto "background_templates" tenemos un array de probabilidades, estas indican los estado de git y personalizan cada uno de ellos, esto hace que al trabajar en un repositorio, si se hacen cambios, se vean de manera visual en la terminal con un cambio de color sencillo y unos iconos.