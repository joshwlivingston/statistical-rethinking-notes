source("rv/scripts/rvr.R")
source("rv/scripts/activate.R")

# Set reticulate to use project venv
local({
  venv_python <- if (.Platform$OS.type == "windows") {
    file.path(getwd(), ".venv", "Scripts", "python.exe")
  } else {
    file.path(getwd(), ".venv", "bin", "python")
  }
  if (file.exists(venv_python)) {
    Sys.setenv(RETICULATE_PYTHON = venv_python)
  }
})
