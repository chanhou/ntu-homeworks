# target run �ΨӴ��զ۳д����ɡA�禬�� Makefile ���|�Ψ�
# �Ѽ� $(PROG) -- ���t path�A���t���ɦW�����յ{���W�� (�p�Gswap)
# �Ѽ� $(DATA) -- ��ơA�N�����ո�ƽs�� (�p�G1)
# run ���ĪG�O�G
#   (1) �ѳo�@�h�� swap.cmm �����ͨ� assembly�A�M���Ķ��������
#   (2) ���J�o�@�h�� swap.cmm.1�A���ͳo�@�h�� swap.cmm.1.out
run: 
	mkdir -p genAsm
	$(MAKE) run -C compiler PROG=$(PROG)
	java -jar ../bass/bass.jar genAsm/$(PROG).bass
	java -cp ".:compiler/lib" $(PROG) < $(PROG).cmm.$(DATA) > $(PROG).cmm.$(DATA).out

# target judgeRun �@�w�n���A�禬�� Makefile �|�Ψ�
# �Ѽ� $(PROG) -- ���t path�A���t���ɦW�����յ{���W�� (�p�Gswap)
# �Ѽ� $(DATA) -- ��ơA�N�����ո�ƽs�� (�p�G1)
# judgeRun ���ĪG�O�G
#   (1) �ѤW�@�h�� swap.cmm �����ͨ� assembly�A�M���Ķ��������
#   (2) ���J�W�@�h�� swap.cmm.1�A���ͳo�@�h�� swap.cmm.1.out
judgeRun: $(PROG).class
	java -cp ".:compiler/lib" $(PROG) < ../$(PROG).cmm.$(DATA) > $(PROG).cmm.$(DATA).out

# �o�� target �O�ΨӹF���W�z�ĪG (1) ��
$(PROG).class:
	mkdir -p genAsm
	$(MAKE) judgeRun -C compiler PROG=$(PROG)
	java -jar ../bass/bass.jar genAsm/$(PROG).bass
	
# target clean �@�w�n���A�禬�� Makefile �|�Ψ�
# clean ���ĪG�����M�� compiler �{�������ɡB���յ{�� assembly �ɡB
#                      ���յ{�������ɡB���յ{�����浲�G
clean:
	$(MAKE) clean -C compiler
	rm -rf genAsm
	rm -f *.class
	rm -f *~
	rm -f *.out
