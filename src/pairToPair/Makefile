UTILITIES_DIR = ../utils/
OBJ_DIR = ../../obj/
BIN_DIR = ../../bin/

# -------------------
# define our includes
# -------------------
INCLUDES = -I$(UTILITIES_DIR)/bedFilePE/ \
           -I$(UTILITIES_DIR)/bedFile/ \
           -I$(UTILITIES_DIR)/lineFileUtilities/ \
           -I$(UTILITIES_DIR)/gzstream/ \
           -I$(UTILITIES_DIR)/version/ \
           -I$(UTILITIES_DIR)/fileType/ \
           -I$(UTILITIES_DIR)/version/

# ----------------------------------
# define our source and object files
# ----------------------------------
SOURCES= pairToPairMain.cpp pairToPair.cpp
OBJECTS= $(SOURCES:.cpp=.o)
_EXT_OBJECTS=bedFilePE.o bedFile.o lineFileUtilities.o gzstream.o fileType.o
EXT_OBJECTS=$(patsubst %,$(OBJ_DIR)/%,$(_EXT_OBJECTS))
BUILT_OBJECTS= $(patsubst %,$(OBJ_DIR)/%,$(OBJECTS))
PROGRAM= pairToPair


all: $(BUILT_OBJECTS)

.PHONY: all

$(BUILT_OBJECTS): $(SOURCES)
	@echo "  * compiling" $(*F).cpp
	@$(CXX) -c -o $@ $(*F).cpp $(LDFLAGS) $(CXXFLAGS) $(INCLUDES)

$(EXT_OBJECTS):
	@$(MAKE) --no-print-directory -C $(UTILITIES_DIR)/bedFile/
	@$(MAKE) --no-print-directory -C $(UTILITIES_DIR)/bedFilePE/
	@$(MAKE) --no-print-directory -C $(UTILITIES_DIR)/lineFileUtilities/
	@$(MAKE) --no-print-directory -C $(UTILITIES_DIR)/gzstream/
	@$(MAKE) --no-print-directory -C $(UTILITIES_DIR)/fileType/	
	
clean:
	@echo "Cleaning up."
	@rm -f $(OBJ_DIR)/* $(BIN_DIR)/*

.PHONY: clean
