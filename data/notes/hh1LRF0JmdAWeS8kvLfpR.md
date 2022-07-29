
http://infochim.u-strasbg.fr/webserv/marvin/help/calculations/s2n.html

## Individual molecules

You can name molecules by using the Naming menu entry of Tools menu in MarvinView, or Structure > Structure to Name > Generate Name in MarvinSketch.
In MarvinSketch, the name can be added to the canvas by using the Structure to Name > Place IUPAC Name entry in the Structure menu. The name will be displayed below the molecule, and updated in real-time when the molecule is modified.

## Batch naming

Naming of a large number of molecules contained in a file can be achieved in two ways: with MarvinView, and on the command line, with molconvert. In both cases, all formats supported by Marvin are acceptable as input.
With MarvinView, open the file containing the structures to be names. Then select the menu File/Save As, and choose "IUPAC Name files" in the "Files of type" drop-down box. Choose a name for the file, and click on the Save button. The file will contain the names of the structures, one per line.

Alternatively, on the command line, you can use the following command:

`molconvert name inputs.mol -o names.txt`

The file names.txt will contain the names of the molecules in the input file, with one name per line.

It is possible to use a format option to chose a nomenclature style:

i (default) uses the IUPAC rules for preferred names;
t uses a more traditional style.

For instance, to generate traditional names, use the following:

`molconvert name:t inputs.mol -o names.txt`

Generate all common names for a structure:

`molconvert "name:common,all" -s tylenol`

Generate the most popular common name for a structure (It fails if none is known.):

`molconvert name:common -s viagra`

Adding names as an additional field to a SDfile can be achieved with the cxcalc tool.

`cxcalc -S name input.sdf -o named.sdf`

## API

For information about how names can be generated from Java programs, see the developer documentation.

## References

IUPAC Provisional Recommendations for the Nomenclature of Organic Chemistry


