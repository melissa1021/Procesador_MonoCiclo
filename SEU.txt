----------------------------------------------------------------------------------
-- Company: 
-- Engineer: 
-- 
-- Create Date:    18:41:51 04/19/2016 
-- Design Name: 
-- Module Name:    SEU - ArquitecturaSEU 
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

entity SEU is
    Port ( EIMM : in  STD_LOGIC_VECTOR (12 downto 0);
           SIMM : out  STD_LOGIC_VECTOR (31 downto 0));
end SEU;

architecture ArquitecturaSEU of SEU is

begin

process (EIMM)

begin

	if(EIMM(12) = '1')then
			SIMM(12 downto 0) <= EIMM;
			SIMM(31 downto 13) <= (others=>'1');
		else
			SIMM(12 downto 0) <= EIMM;
			SIMM(31 downto 13) <= (others=>'0');
		end if;

end process;


end ArquitecturaSEU;

