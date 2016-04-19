----------------------------------------------------------------------------------
-- Company: 
-- Engineer: 
-- 
-- Create Date:    18:38:02 04/11/2016 
-- Design Name: 
-- Module Name:    NPC - ArquitecturaNPC 
-- Project Name: 
-- Target Devices: 
-- Tool versions: 
-- Description: 
--
-- Dependencies: 
--
-- Revision: 
-- Revision 0.01 - File Created
-- Additional Comments: 
--
----------------------------------------------------------------------------------
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

-- Uncomment the following library declaration if using
-- arithmetic functions with Signed or Unsigned values
--use IEEE.NUMERIC_STD.ALL;

-- Uncomment the following library declaration if instantiating
-- any Xilinx primitives in this code.
--library UNISIM;
--use UNISIM.VComponents.all;

entity NPC is
    Port ( Vreset : in  STD_LOGIC;
           Vdin : in  STD_LOGIC_VECTOR (31 downto 0);
           Vclk : in  STD_LOGIC;
           Vdout : out  STD_LOGIC_VECTOR (31 downto 0));
end NPC;

architecture ArquitecturaNPC of NPC is

begin
process(Vreset, Vdin, Vclk)

begin

if(Vreset='1') then 
	Vdout <= "00000000000000000000000000000000";
else
	if(rising_edge(Vclk)) then 
		Vdout <= Vdin;
	end if;
end if;

end process;

end ArquitecturaNPC;

