# Flip Flop and HA

` --  https://electronicstopper.blogspot.com/2017/07/t-flip-flop-in-vhdl-with-testbench.html
LIBRARY ieee;
USE ieee.std_logic_1164.ALL;

ENTITY TFF_tb IS
END TFF_tb;

ARCHITECTURE behavior OF TFF_tb IS 

    component ha
        port( a, b : in std_logic; s, c: out std_logic);
    end component;

    COMPONENT TFF
    PORT(
         T : IN  std_logic;
         clk : IN  std_logic;
         rst : IN  std_logic;
         Q : buffer  std_logic;
         set : in std_logic
        );
    END COMPONENT;
    
   signal T : std_logic := '0';
   signal clk : std_logic := '0';
   signal rst : std_logic := '0';
   signal set :std_logic;
   signal Q : std_logic;
   signal a : std_logic := T;
   signal b : std_logic := clk;
   
   constant clk_period : time := 10 ns;

BEGIN
   uut: TFF PORT MAP (
          T => T,
          clk => clk,
          rst => rst,
          Q => Q,
          set => set
        );

  clk_process : process
  begin
  clk <= '0';
  wait for clk_period/2;
  clk <= '1';
  wait for clk_period/2;
  if NOW > 200 ns then
  wait;
  end if;
  end process;

  stim_proc: process
  begin  
 
  rst <= '1';
  wait for 50 ns; 

  rst <= '0';
  T <= '0';
  wait for 50 ns;
  
  rst <= '0';
  T <= '1';  
  wait for 50 ns;

  rst <= '1';
  wait;

  end process;

END; `

--------------------------------------------------------------------------------------------------
## T Flip Flop

` --  https://electronicstopper.blogspot.com/2017/07/t-flip-flop-in-vhdl-with-testbench.html
library ieee;
use ieee.std_logic_1164.all;

entity TFF is
port( T: in std_logic;
clk: in std_logic;
rst: in std_logic;
set: in std_logic;
Q: buffer std_logic);
end TFF;

architecture behavioral of TFF is
begin
process(rst,clk,T,set)
begin

if (rst='1' or set='0' or set='1') then
if (set='0' or set='1') then
Q<=set;
elsif(rst='1') then
Q<='0';
end if;

elsif(rising_edge(clk) and T='1') then
Q<=not Q;

end if;
end process;

end behavioral;`

--------------------------------------------------------------------------------------------------
### Half Adder

~ -- Binary half adder (HA)
-- Author: Nerdy Dave
-- Source: https://youtu.be/H2GyAIYwZbw
library ieee;               
use ieee.std_logic_1164.all;

entity ha is
    port
    (
        a:  in  std_logic; 
        b:  in  std_logic; 
        s:  out std_logic; -- Output sum of a and b
        c:  out std_logic  -- Output carry
    );
end ha;

architecture behave of ha is
begin
    s <= a xor b;
    c <= a and b;
end behave;
~
