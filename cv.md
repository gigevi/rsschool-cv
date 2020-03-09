**Sofinsky Dmitry.**
Mobile phone +375297199486
VK https://vk.com/dimasofico
dsofinskiy@gmail.com
I want to know more about android development. I want to learn how to work in a team and write large and interesting client-server applications. I love to study and am ready to spend all my free time on an interesting field of activity for me.
Android API, Java, XML, C.

#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include "changer.h"

// Disable persistent recommendations microsoft
#if defined(_WIN32) || defined(__WIN32__) || defined(WIN32)
#define _CRT_SECURE_NO_WARNINGS
#pragma warning(disable:4996)
#endif
FILE* fileOpen(char* fileName, char* mode);

int main(int argc, char* argv[])
{
	FILE* rulesFile = NULL;
	FILE* inputFile = NULL;
	FILE* outputFile = NULL;

	// Check for arguments
	if (argc == 1) {
		help();
		return 0;
	}

	// Catch --help or -h
	for (int i = 1; i < argc; i++) {
		if (!strcmp(argv[i], "-h") || !strcmp(argv[i], "--help")) {
			help();
			return 0;
		}
	}

	

	int i = 1;

	while (i < argc)
	{
		if (!strcmp(argv[i], "-r") || !strcmp(argv[i], "--rule")) {
			rulesFile = fileOpen(argv[++i], "r");
		}
		else if (!strcmp(argv[i], "-i") || !strcmp(argv[i], "--input")) {
			inputFile = fileOpen(argv[++i], "r");
		}
		else if (!strcmp(argv[i], "-o") || !strcmp(argv[i], "--output")) {
			outputFile = fileOpen(argv[++i], "w");
		}
		i++;
	}


	if (checkArguments(inputFile, outputFile, rulesFile))
		modifyPasswords(inputFile, outputFile, rulesFile);

}

int checkArguments(FILE* inputFile, FILE* outputFile, FILE* rulesFile)
{
	if (inputFile == NULL) {

		puts("No input file");
		return 0;
	}
	else if (outputFile == NULL) {
		puts("No output file");
		return 0;
	}
	else if (rulesFile == NULL) {
		puts("No rules file");
		return 0;
	}
	return 1;
}


// open the file, in case of an error close the program with an information message
FILE* fileOpen(char* fileName, char* mode)
{
	FILE* file;
	if ((file = fopen(fileName, mode)) == NULL)
	{
		printf("Couldn't open the %s file", fileName);
		exit(1);
	}
	else
		return file;
}



help()
{
	printf("\nPassModify OPTIONS\n\n");
	printf("-h, --help              Display this message\n");
	printf("-r, --rule              File with change rules\n");
	printf("-i, --input             File with passwords\n");
	printf("-o, --output            Write passwords to FILE, one per line\n");
}

Mobile application for time management.
BSUIR FCAD, Information Systems and Technologies for Industrial Safety
English: A2+