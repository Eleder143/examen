
# carga de librerias
library(httr)
library(jsonlite)
library(tidyverse)


# carga de datos
bancos <- function(x) {
  cbind(
    fromJSON(rawToChar(GET(
      url = paste0("https://www.givefood.org.uk/api/2/foodbanks/search/?address=", x)
    )$content)),
    fromJSON(rawToChar(GET(
      url = paste0("https://www.givefood.org.uk/api/2/foodbanks/search/?address=", x)
    )$content))$needs
  )
}


bancos_localidad <- bancos("Manchester")

# para info
# summary(bancos_localidad$found)

# cambiar la fecha a formato Date
bancos_localidad$found <- as.Date(bancos_localidad$found)

# obtener el id del banco mas antiguo
id_banco_mas_antiguo <- bancos_localidad[which.min(bancos_localidad$found), "id"]

# obtener las necesidades del banco mas antiguo
print(list(bancos_localidad[which.min(bancos_localidad$found), "needs"]$needs))
